---
title: "C++ General Help on Apps, and MonoDevelop"
date: 2008-06-26
forum: General Help
---

### Post by Mr.Useless on 2008-06-26
Hello, I would just like to request a bit of information on C++ with linux.

I would like to know which piece of software is the most used for programming in this language. I was recommended by a friend to get MonoDevelop, which so far i have found the GUI fairly easy to use and have got used to that aspect of the program easily.

Bare in mind i have just started to learn, so the images i am posting are what i hav been learning from the tutorial site:
Cplusplus.com
(If anyone know any others i would appreciate it, they seem similar i just am not too keen on the layout of Cplusplus.com)

I have a couple of questions, when i click run to test what i have written I get the error:

Building Project: HelloWorld (Debug)

Build failed. Object reference not set to an instance of an object

In the console at the bottom (Build Output). Does anyone know what i could be doing wrong? or possibly what I am writing is incompatible with this software (cant see how C++ would ever vary from system to system, but YOU NEVER KNOW! well I don't)

I will post some pictures (ill try anyway) now

---

### Post by KingTermite on 2008-06-26
There is a forum for programming stuff...this thread will probably get moved there, FYI.

I'm not familiar with monodevelop. Does it use g++ underneath? The main cpp compiler.

I notice that there is a * by the file name. Did you actually save the file before trying to compile? It looks pretty simple and correct from a quick glance.

---

### Post by Mr.Useless on 2008-06-26
Ahh must have missed that forum i had a quick skim, for one, sorry about that, ill try saving it again and doing it but i did before :S

Thanks for reply 

Ryan

---

### Post by KingTermite on 2008-06-26
if you still have trouble, try g++ from the command line.

g++ hello.cpp

then run the a.out file it creates (./a.out).

If you don't have g++ installed, install the entire GCC package with:
sudo apg-get install build-essential

---

### Post by Mr.Useless on 2008-06-26
i cant run it or build it its only in MonoDevelop, ill have a look around for other C++ Dev's i cant see there being a problem with this but it wont harm anyone if i look for another :D

Thanks same SS as before for when i try to build the code, not just run it

Ryan

---

### Post by Mr.Useless on 2008-06-26
Sorry i forgot to mention im pretty much a noob to linux i know a few terminal commands, mostly sudo apt-get install **********

and how to install stuff manusally through ./configure n stuff but
this G++ thing is installed doesnt find cpp file (cos there isnt ne, no problem with g++) 

Ryan

---

### Post by Mr.Useless on 2008-06-26
I got that command to worked, and yeh the it worked..

```
ryan@Ryan-Linux:~$ g++ HelloWorld.cpp
HelloWorld.cpp:12:2: warning: no newline at end of file
ryan@Ryan-Linux:~$ ./a.out
Hello World! I'm a C++ programryan@Ryan-Linux:~$ 

```

But still a gui type thing would be nice, for testing and debugging

Ryan

---

### Post by Mr.Useless on 2008-06-26
Heard of eclipse? im downloading it now its the top recommended so it should be a bit more friendly i hope!

Ryan

---

### Post by KingTermite on 2008-06-27
Be warned, I think Eclipse needs a plugin for C++ (not sure if its in there by default or not). Eclipse was designed for Java.

There are plenty of other IDEs to try. If you are just doing normal/simple C++ learning stuff, I'd just suggest using a good editor (like geany) and not bothering with a full up IDE which will have its own learning curve.

---

### Post by mali2297 on 2008-06-27
[Anjuta]("http://anjuta.sourceforge.net/") is an IDE for C and C++.

---

### Post by Gunman1982 on 2008-06-27
If you want to really learn C/C++ use an editor. Many IDE's already do fancy stuff in the background or give you code completition or something like that. Its easier to start but you don't learn as much imho.

---

### Post by Mr.Useless on 2008-06-27
Thanks for the response, i will deifnatly take a look at those two. i got the plugin for eclipse, it seems to be more of like microsofts visualC++ enterprise with its managment n stuff.

Thanks, if i get any trouble i will be sure to post what im struggling with (Y)

---

### Post by WRDN on 2008-06-27
Monodevelop is used to compile C# primarily.
For C++ programming, I personally use [Code::Blocks]("http://www.codeblocks.org/").

---

### Post by tyfius on 2008-06-27
My favorite at the moment is CodeBlocks.

---

