---
title: "How to install ChatScript on Ubuntu?"
date: 2017-10-20
forum: General Help
---

### Post by rezaee on 2017-10-20
Hi
 I am newbie in Linux. I like to compile and use ChatScript program on my Ubuntu16.04, as the tutorial says here: [https://github.com/bwilcox-1234/ChatScript/blob/master/WIKI/CLIENTS-AND-SERVERS/ChatScript-External-Communications.md](https://github.com/bwilcox-1234/ChatScript/blob/master/WIKI/CLIENTS-AND-SERVERS/ChatScript-External-Communications.md)
 > 
**Embedding Step #1**

 First, you will need to modify common.h and compile the system. You need to add all the CS .cpp files to your build list.

 Find the // #define NOMAIN 1 and uncomment it. This will allow you to compile your program as the main program and ChatScript merely as a collection of routines to accompany it. 

 

 But I can not understand this part " **You need to add all the CS .cpp files to your build list.**"
 What is my build list? how can I add .cpp to it?

 I tried to compile the source file(as you can see it here: [https://github.com/bwilcox-1234/ChatScript/tree/master/SRC](https://github.com/bwilcox-1234/ChatScript/tree/master/SRC)), by ```
make server
``` command as tutorial says, but 
 I got this error message: 

 ```
/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/crt1.o: In function `_start':
 (.text+0x20): undefined reference to `main'
 collect2: error: ld returned 1 exit status
 Makefile:107: recipe for target 'binary' failed
 make: *** [binary] Error 1
```

 I asked the author from this error and he said: 
 > it was all well and good BUT  you dont have your own C++ program also in  the list of files and YOUR code would have a main program

 But I couldn't understand what he says and how can I solve it?

 Also the full result of my execution output is visible here: [https://github.com/bwilcox-1234/ChatScript/issues/171](https://github.com/bwilcox-1234/ChatScript/issues/171)

 I really need help and want to compile and run it...please help me if you can ](*,)

---

### Post by coffeecat on 2017-10-20
Duplicate here:

[https://ubuntuforums.org/showthread.php?t=2374835](https://ubuntuforums.org/showthread.php?t=2374835)

Please do not create duplicate threads in different parts of the forum. I you think a thread you create would do better in another section, please use the report button in your own post to send a move request to the staff area.

Thread closed.

---

