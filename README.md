Download Link: https://assignmentchef.com/product/solved-cs201-homework-1b
<br>
In this homework, you will implement a bookstore system to store multiple books. Each book has its title, its price, and a list of the years of its editions. The books in the bookstore system and the list of their edition years have to be implemented using <strong><u>dynamically allocated arrays</u></strong>. The homework has two parts whose requirements are explained below.

<strong>PART A: </strong>

<strong>To take the final exam, you must submit this part and receive at least half of its points. </strong>

This part includes the implementation of the Book class, which is used to implement a single book. This class stores the title and price of the book as well as a list of the years of its editions (please see the data members of the given Book class definition). The list of the edition years has to be stored in a dynamically allocated array of integers. You will use this class definition and implementation in Part B of your homework.

Note that this class definition has to be stored in a header file named Book.h. This header file is provided to you and you are <u>not allowed to change</u> the contents of this file.




<table width="642">

 <tbody>

  <tr>

   <td width="642">#ifndef __BOOK_H#define __BOOK_H #include &lt;string&gt;class Book{ public:Book( const string bookTitle = “”, const double bookPrice = 0 );Book( const Book&amp; bookToCopy );~Book();Book&amp; operator=( const Book&amp; right );    void addEdition( const int newEditionYear );private:string title;        // Title of the book    double price;     // Price of the bookint editionNo;       // Number of the editions of the bookint* editionYears; // A list of the years of the book’s editions// Note that each book can have zero or more editions // BookStore class, which you will implement in Part B, is declared as friend friend class BookStore; // Overloaded global functions for &gt;&gt; and &lt;&lt; are declared as friend friend istream&amp; operator&gt;&gt;( istream&amp; in, Book&amp; b ); friend ostream&amp; operator&lt;&lt;( ostream&amp; out, const Book&amp; b ); }; #endif</td>

  </tr>

 </tbody>

</table>

You need to implement each of the given functions in a source file named Book.cpp. The details of these functions are given below:

<ul>

 <li>The constructor initializes the title and the price of the book with the provided arguments. If none provided, the default values of “” and 0 should be used, as given in the class definition. This constructor needs to create an empty array for the years of the book’s editions.</li>

 <li>The destructor needs to be implemented to avoid memory leaks.</li>

 <li>The copy constructor and the assignment operator need to perform a deep copy operation.</li>

 <li>The addEdition function adds an edition year to the book. Edition years do not need to be unique.</li>

 <li>The operator&lt;&lt; function is a global function that outputs the information of the book object given on the right hand side of &lt;&lt;. Your output should exactly have the format given below. Otherwise, you will lose points.</li>

</ul>

The first line gives the format when the number of editions is zero. The second line gives the format when there is one edition. The third line gives the format when there are more than one edition. You can find examples in the OutputPartA.txt file, which includes the output of an example code given in the mainPartA.cpp file.

<em>title-of-the-book</em>, <em>price-of-the-book</em> TL (none) <em>title-of-the-book</em>, <em>price-of-the-book</em> TL (<em>1st-year</em>)

<em>title-of-the-book</em>, <em>price-of-the-book</em> TL (<em>1st-year</em>, <em>2nd-year</em>, <em>…</em>, <em>last-year</em>)

<ul>

 <li>The operator&gt;&gt; function is a global function that inputs the edition years of the book object given on the right hand side of &gt;&gt;. This function needs to input all edition years typed in a single line terminated by a new line character. The edition years are separated with whitespace characters. Here you may assume that the user only inputs digits and whitespace characters. Note that if this line just includes whitespace characters (without any digits) or if it is empty, the given book object will have an empty list of edition years. Some input examples are provided at the end of thecpp file.</li>

</ul>

The operator&gt;&gt; function overwrites the edition years of the book object given on the right hand side of &gt;&gt;. That is, before getting the new edition year(s) from the input stream, you have to delete the existing edition years of the given object to avoid memory leaks.

This function requires getting all of the characters in a single line into a string and tokenizing the string into individual years (which are of the integer type). As a part of this homework, every student will study and learn (by his/her own) how to use the string functions and/or how to manipulate strings in order to extract the required tokens from a given string.




<strong> </strong>

<strong> </strong>

<strong>PART B (70 points): </strong>

<strong> </strong>

This part includes the implementation of the BookStore class. This class stores the number of the books in the bookstore system and the book objects (please see the data members of the given BookStore class definition). The book objects have to be stored in a dynamically allocated array.




Note that this class definition has to be stored in a header file named BookStore.h. This header file is provided to you and you are <u>not allowed to change</u> the contents of this file.




<table width="642">

 <tbody>

  <tr>

   <td width="642">#ifndef __BOOKSTORE_H#define __BOOKSTORE_H #include “Book.h”class BookStore{ public:BookStore();BookStore( const BookStore&amp; bsToCopy );~BookStore();BookStore&amp; operator=( const BookStore&amp; right );Book&amp; operator[]( const string title ); void addBook( const string bookTitle, const double bookPrice );    void removeBook( const string bookTitle );private:Book* books;  // A dynamically created array of book objects    int bookNo;     // Number of the books in the bookstore system // Overloaded global function for &lt;&lt; is declared as friend friend ostream&amp; operator&lt;&lt;( ostream&amp; out, const BookStore&amp; b ); }; #endif</td>

  </tr>

 </tbody>

</table>




You need to implement each of the given functions in a source file named BookStore.cpp. The details of these functions are given below:

<ul>

 <li>The constructor creates an empty array of books.</li>

 <li>The destructor needs to be implemented to avoid memory leaks.</li>

 <li>The copy constructor and the assignment operator need to perform a deep copy operation.</li>

 <li>The overloaded subscript operator takes a title as its input parameter and returns the book object with this title. It returns the book object by reference such that the returned object can be used as an r-value as well as an l-value. This overloaded operator throws an exception if its argument is invalid. In other words, it throws an exception if the bookstore system does not have a book with the given title.</li>

 <li>The addBook function adds a new book to the bookstore system. The title and the price of the book are specified as input parameters. This function does not add any edition years; that is, the edition years of the book should be initialized with an empty array. The book titles are unique (case sensitive). If the system already has a book with the specified title, this function does not add this book to the system and throws an exception.</li>

 <li>The removeBook function removes an existing book from the bookstore system. The title of the book is specified as an input parameter. It also clears the edition years of the specified book. If the system does not have a book with the specified title, this function throws an exception.</li>

 <li>The operator&lt;&lt; function is a global function that outputs the information of all of the books in the bookstore object given on the right hand side of &lt;&lt;. Its output should contain an output line for</li>

</ul>

each book; the format of this line has been explained in Part A. You can also find examples in the OutputPartB.txt file, which includes the output of an example code given in the mainPartB.cpp file.


