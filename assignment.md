
In computer science, binary search, also known as half-interval search, is an efficient search algorithm that finds the position of a target value within a sorted array, by comparing the target value to the middle element, and then repeating the process by splitting that half of the subarray again,  and so on until the target is found. 
In the image above,  Mario searches the sorted treasure boxes by optimizing his work by starting at the middle, then the middle again, until locates the treasure,  in this case in only three steps. Not only a good jumper, but he's smart too!
BinarySearch is much faster than linear search,  for large arrays.  A linear search is a search that starts from the top and searches all items or until the item is found, like looking for a name in a phonebook by starting from the beginning until the name is found. 
Fun Facts
In Iceland,  phonebooks are alphabetized in first-name order because Icelanders don't use family names, rather they use first names as follows:  
 A newborn baby, for example, may be given the first name Oluf or Joanna by his parents, and if his father’s first name is Jón, the baby will have the surname Jónsson. So his full name will be Oluf Jónsson or Joanna Jónsson.  When Oluf Jónsson grows up and has children of his own, his son will have the last name Olufsson.
ICELANDIC LAST NAMES: HOW DO THEY WORK?Links to an external site.
So phone books can be a problem in Iceland.  Luckily the population of the whole country in 2020 was only 36600, not hundreds of millions,  but even then, that's a pretty big phonebook.  
Both simple arrays and ArrayLists have built-in implementations of binary search, but to use binarySearch, in either data structure,  as we have seen,  the list must be sorted. 
 
Efficient searching is a major topic in Data Structures and Algorithms so this assignment will give you a basic understanding of some of the fundamentals of efficient searching and more practice with arrays and ArrayLists. 
  
For this project, you will create two classes representing two data structure components for searching and managing lists of integers.  The two classes from the user's point of view share identical interfaces and operations but have very different underlying data structures,  one using a simple array of integers, the other an ArrayList of type Integer. 
You should read up on interfaces if you are unfamiliar.  An interface provides a template for defined behavior to a class that inherits from the interface. The implementation is left to the implementing class.   A  class that implements an interface must implement  ALL  the methods declared in the interface, unless the class inherits from another class that already implements one or more of those methods.   
binarySearch
The two classes you will create will implement the operations defined in the interface as shown in the UML class diagram above.  
In addition,  BinarySearchArray will implement a method testBinarySearch() that populates the lists,  and lets the user interactively test the two classes by adding and removing elements.  The parameter BinarySearch can represent either class and tells testBinarySearchArray which class to test.  

Optional starter file here:

Use a starter file if you must, or better, challenge yourself by just using the following documentation. 

Steps to Implement if you are writing your code from scratch (recommended):    
 To get started create a new project in IntelliJ called BinarySearch.
Add a class to your project called BinarySearchArray.
Then add another class  BinarySearchArrayList.
Add an interface named BinarySearch.   The interface BinarySearch should include the public method stubs as shown in the diagram.  
Your two classes should implement the interface. 
You can have all classes and the interface in the same file.  Only the class with the main class can be public.  Only the class containing the main method can be defined as public in files defining multiple classes.     
Here is what you should have in your file:  
interface BinarySearch {
    public int binarySearch(int key);
    public void printElements();
    public void remove(int index);
    public void add(int value);
    public boolean contains(int value);
    public void initializeArray();
    public void sort();
}

public class BinarySearchArray implements BinarySearch {
}

class BinarySearchArrayList implements BinarySearch{
}
Using an interface is very convenient for this project, because different classes that implement the same interface solve a similar problem but in a very different way  The interface is a promise of certain general behavior, and the concrete class provides the concrete specialized implementation.  We have two lists of numbers, one stored in an array, the other in an ArrayLIst so manipulating the two data structures is very different, but the interface is the same. 
These methods will have the same signature as the interface but may be implemented very differently,  (See below)
How to implement the interface with Arrays and ArrayList 
Method Name	Arrays - How to implement	Comments	ArrayList	Comments
sort	Arrays.sort()	import java.util.Arrays	Collections.sort	import java.util.Collections
binarySearch	Arrays.binarySearch()	Arrays.binarySearch(arr,key). Returns a negative number if not present, otherwise, return index.  	Collections.binarySearch()	Collections.binarySearch(arrList, key)
remove(index)	No API method available requires	Requires shifting up items below item being remove. 	remove(index)	
arrList.remove(index);
boolean contains(value)	
Use binarySearch or a for loop to
determine if the key is present in the array.
No api method. 

binarySearch return a negative number if not present, otherwise returns index. 	boolean contains(value) 	
arrList.contains(Integer.valueOf(value))
add(int value) 	No api method available	An "empty" element is marked by a zero value.  If no zeros, print an error message "no space available"	add(int value) 	
arrList.add(value);
initializeArray() 
initializeArray()	Same as array class.  
printElements()
No api method available 	Prints the elements of the array on a single line delimited by spaces and newline at end of line.   Uses arr. 	printElements()	Prints the elements of the array on a single line delimited by spaces and newline at end of line.   Uses arrList. 
public static void testBinarySearchArray
(BinarySearch searchObject)
This method is part of BinarySearchArray
class. 
Use bsArr for parameters
See the discussion below on how to implement. 	Test driver method to be called from main.  Takes parameter of BinarySearch which indicates the method which class to test.  	 Same as array versions	Use static method BinarySearchArray. testBinarySearchArray(bsArrList)
 intializeArray, add, remove		For both array and ArrayList,  call sort and printElements after each of these methods.  	 	For both array and arrayList,  call sort and printElements after each of these methods.
main()  from class BinarySearchArray	
BinarySearchArray bsArr = 
new BinarySearchArray();
bsArr.initializeArray();
bsArr.sort();
bsArr.printElements();
BinarySearchArray.testBinarySearchArray(bsArr);
 	
BinarySearchArrayList bsArrList = new BinarySearchArrayList();
bsArrList.initializeArray();
bsArrList.sort();
bsArrList.printElements();
BinarySearchArray.testBinarySearchArray(bsArrList);
Interactive Test Driver testBinarySearchArray()   

Use a while loop to interactively test the array or ArrayList. Array has a capacity limit that requires error checking while ArrayList does not .

Instructions for using starter file: 
If you must see the starterfile here:  (Sometimes it takes a  while to download). 

 The download does include the completed test driver but will require you to write code for key methods. It will say:  "Add your code here".  Remember to sort and print your list after items your list is changed.  Adding an item will require that the list be re-sorted. 

 

TestBinarySearch  - this is used by both the simple array and arrayList versions. 
public void testBinarySearch(BinarySearch searchObject) {
    Scanner scanner = new Scanner(System.in);
    int value = 0;
    while (value != -1)
    {
        System.out.print("Enter an integer to search (or -1 to quit): ");
        String ss = scanner.nextLine();
        value = Integer.parseInt(ss);
        if (value == -1) {
            break;
        }
        int index;
        if ((index = searchObject.binarySearch(value)) >= 0) {
            System.out.println("Value " + value + " found." + " Do you want to remove it? y/n? ");
            String answer = scanner.nextLine();
            if (answer.equals("y")) {
                searchObject.remove(index);
            }
        } else {
            System.out.println("Value " + value + " not found." + " Do you want to add it? y/n? ");
            String answer = scanner.nextLine();
            if (answer.equals("y"))
                searchObject.add(value);
        }
    }
    System.out.println("Goodbye...");
}

This is the testDriver called from main: 
public void binarySearchTestDriver()  {
    System.out.println();
    BinarySearch bsArr = new BinarySearchArray();
    bsArr.initializeArray();
    bsArr.sort();
    String mode = bsArr.getClass().getSimpleName();
    printWelcomeMessage(mode);
    bsArr.printElements();
    testBinarySearch(bsArr);

    bsArr = new BinarySearchArrayList();
    bsArr.initializeArray();
    bsArr.sort();
    mode = bsArr.getClass().getSimpleName();
    printWelcomeMessage(mode);
    bsArr.printElements();
    testBinarySearch(bsArr);
}
 

Sample output.  This runs the Simple Array Binary Search followed by ArrayList Version.  Make sure you run both parts of the program,  Simple Array and ArrayList!

Welcome to the Binary Search Test (Simple Array):

Search Elements:
0 0 0 0 0 1 4 6 11 14 16 18 20 21 24 

Enter an integer to search (or -1 to quit): 7
Value 7 not found. Do you want to add it? y/n? 
y
Search Elements:
0 0 0 0 1 4 6 7 11 14 16 18 20 21 24 

Enter an integer to search (or -1 to quit): 3
Value 3 not found. Do you want to add it? y/n? 
y
Search Elements:
0 0 0 1 3 4 6 7 11 14 16 18 20 21 24 

Enter an integer to search (or -1 to quit): 3
Value 3 found. Do you want to remove it? y/n? 
y
Search Elements:
0 0 0 0 1 4 6 7 11 14 16 18 20 21 24 

Enter an integer to search (or -1 to quit): 5
Value 5 not found. Do you want to add it? y/n? 
y
Search Elements:
0 0 0 1 4 5 6 7 11 14 16 18 20 21 24 

Enter an integer to search (or -1 to quit): -1
Goodbye...


Welcome to the Binary Search Test (ArrayList):

5 6 10 13 14 18 19 21 22 25 
Enter an integer to search (or -1 to quit): 7
Value 7 not found. Do you want to add it? y/n? 
y
5 6 7 10 13 14 18 19 21 22 25 
Enter an integer to search (or -1 to quit): 20
Value 20 not found. Do you want to add it? y/n? 
y
5 6 7 10 13 14 18 19 20 21 22 25 
Enter an integer to search (or -1 to quit): -1
Goodbye...

Important:  Please Answer the Following Questions in Submission Comments or Attachment:  
Questions:  (Please add your answers to your Canvas assignments comments); 

Why does the simple array version include zeros in the printout?  What happens if you keep adding until there are no more zeros?  Can you add another new item after all the zeros are filled?  Why or why not? How does this contrast with the ArrayList version?
 Why do we use an interface in this program?  What is the difference between the ArrayList and the Simple Array version of the testBinarySearchArray?  Is there some reason why this is?  Why does testBinarySearchArray take BinarySearch as a parameter?  
