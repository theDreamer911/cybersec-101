# Introduction

Every one of us uses different programs on our computers. Generally speaking, programs run on our computers, using our computer’s processing power and storage. Moreover, to use a program, we need to install it first. What if we can use any program without installation?

A web application is like a “program” that we can use without installation as long as we have a modern standard web browser, such as Firefox, Safari, or Chrome. Consequently, instead of installing every program you need, you only need to browse the related page. The following are some examples of web applications:

* Webmail such as Tutanota, Protonmail, Outlook, and Gmail
* Online office suites such as Microsoft Office 365 (Word, Excel, and PowerPoint), Google Drive (Docs, Sheets, and Slides), and Zoho Office (Writer, Sheet, and Show)
* Online shopping such as Amazon.com, AliExpress, and Etsy

Thousands more examples provide a myriad of services. Other examples include online banking, money transfer, weather forecast, and social media.

<a align="center">![image](https://user-images.githubusercontent.com/71202864/212443107-0e52a3ff-afd9-4a02-b860-eb01c9f0d393.png)</a>

The idea of a web application is that it is a program running on a remote server. A server refers to a computer system running continuously to “serve” the clients. In this case, the server will run a specific type of program that can be accessed by web browsers.

Consider an online shopping application. The web application will read the data about the products and their details from a database server. A database is used to store information in an organized way. Examples include information about products, customers, and invoices. A database server is responsible for many functions, including reading, searching, and writing to the database. The online shopping web application might need more than one database to access, for example:

* Products database: This database contains details about the products, such as name, images, specifications, and price.
* Customers database: It contains all details related to customers, such as name, address, email, and phone number.
* Sales database: We expect to see what each customer has purchased and how they paid in this database.

We can already see the amount of information stored in any online shopping system. Suppose an attacker manages to exploit (hack) the web application and steal the customers’ database. In that case, this will lead to a significant loss for the company and its customers.

The image below shows searching for an item on an online shopping site. In the simplest version, the search will take four steps:

1. The user enters an item name or related keywords in the search field. The web browser sends the search keyword(s) to the online shopping web application.
2. The web application queries (searches) the products database for the submitted keywords.
3. The product database returns the search results matching the provided keywords to the web application.
4. The web application formats the results as a friendly web page and returns them to the user.

<a align="center">![image](https://user-images.githubusercontent.com/71202864/212443158-8550ccbc-e484-4931-b8ea-5046e9628917.png)</a>

From the user’s perspective, they will only access an elegant online shop where all the technical infrastructure is hidden.

<a align="center">![image](https://user-images.githubusercontent.com/71202864/212443170-3ad67ade-33d3-46b8-8eb5-0944109927c6.png)</a>

Many companies offer bug bounty programs. A bug bounty program allows the company to offer a reward for anyone who discovers a security vulnerability (weakness) in the company’s systems. The main condition is that the found vulnerability is within the bug bounty scope and rules. Among many others, Google, Microsoft, and Facebook have bug bounty programs. Discovering a bug can earn you from a few hundred USD to tens of thousands of USD, depending on the severity of the vulnerability, i.e., the weakness you discovered.

# Common Web Application Security Risks

Let’s say that you want to buy an item from an online shop. There are certain functions that you would expect to be able to do on this web application. Most straightforwardly, the online order might go as follows:

<a align="center">![image](https://user-images.githubusercontent.com/71202864/212443225-d0488bad-1d4b-415f-921f-0550dd65cc8e.png)</a>

There are a few main categories of common attacks against web applications. Consider the following steps and related attacks.

* Log in at the website: The attacker can try to discover the password by trying many words. The attacker would use a long list of passwords with an automated tool to test them against the login page.
* Search for the product: The attacker can attempt to breach the system by adding specific characters and codes to the search term. The attacker’s objective is for the target system to return data it should not or execute a program it should not.
* Provide payment details: The attacker would check if the payment details are sent in cleartext or using weak encryption. Encryption refers to making the data unreadable without knowing the secret key or password.

We cannot cover everything, but we will present a few formal categories from OWASP Top Ten. Don’t worry if these techniques sound alien to you; TryHackMe walks you through each vulnerability.

## Identification and Authentication Failure
Identification refers to the ability to identify a user uniquely. In contrast, authentication refers to the ability to prove that the user is whom they claims to be. The online shop must confirm the user’s identity and authenticate them before they can use the system. However, this step is prone to different types of weaknesses. Example weaknesses include:

* Allowing the attacker to use brute force, i.e., try many passwords, usually using automated tools, to find valid login credentials.
* Allowing the user to choose a weak password. A weak password is usually easy to guess.
* Storing the users’ passwords in plain text. If the attacker manages to read the file containing the passwords, we don’t want them to be able to learn the stored password.

| Username | Password |
| -------- | -------- |
| Ando | freewill1 |
| Ben | QWmnkL12! |
| Lucy | superman123 |

## Broken Access Control
Access control ensures that each user can only access files (documents, images, etc.) related to their role or work. For example, you don’t want someone in the marketing department to access (read) the finance department’s documents. Example vulnerabilities related to access control include:

* Failing to apply the principle of the least privilege and giving users more access permissions than they need. For example, an online customer should be able to view the prices of the items, but they should not be able to change them.
* Being able to view or modify someone else’s account by using its unique identifier. For example, you don’t want one bank client to be able to view the transactions of another client.
* Being able to browse pages that require authentication (logging in) as an unauthenticated user. For example, we cannot let anyone view the webmail before logging in.

## Injection
An injection attack refers to a vulnerability in the web application where the user can insert malicious code as part of their input. One cause of this vulnerability is the lack of proper validation and sanitization of the user’s input.

## Cryptographic Failures
This category refers to the failures related to cryptography. Cryptography focuses on the processes of encryption and decryption of data. Encryption scrambles cleartext into ciphertext, which should be gibberish to anyone who does not have the secret key to decrypt it. In other words, encryption ensures that no one can read the data without knowing the secret key. Decryption converts the ciphertext back into the original cleartext using the secret key. Examples of cryptographic failures include:

* Sending sensitive data in clear text, for example, using HTTP instead of HTTPS. HTTP is the protocol used to access the web, while HTTPS is the secure version of HTTP. Others can read everything you send over HTTP, but not HTTPS.
* Relying on a weak cryptographic algorithm. One old cryptographic algorithm is to shift each letter by one. For instance, “TRY HACK ME” becomes “USZ IBDL NF.” This cryptographic algorithm is trivial to break.
* Using default or weak keys for cryptographic functions. It won’t be challenging to break the encryption that used 1234 as the secret key.

Sources: [TryHackMe](https://tryhackme.com/room/introwebapplicationsecurity)

