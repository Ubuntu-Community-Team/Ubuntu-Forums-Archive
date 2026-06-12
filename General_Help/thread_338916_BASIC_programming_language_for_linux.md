---
title: "BASIC programming language for linux?"
date: 2007-01-15
forum: General Help
---

### Post by Coop on 2007-01-15
Hello
When I was in class 6,I did programming in a computer language called BASIC,which had commands like "10 let something = something".
Is there a linux version of BASIC?If there is how do I download and install it?
Please reply to me.
Ahmed

---

### Post by lothar_m on 2007-01-15
try real basic. it has a linux version.
[http://www.realbasic.com/]("http://www.realbasic.com/")

---

### Post by feest on 2007-01-15
if you mean visual basic you can try gamba's 
real basic should do the job for the original basic

---

### Post by Coop on 2007-01-15
Hello
Real basic isn't free.I want a BASIC that is free.
Please tell me a BASIC that is free.
Ahmed

---

### Post by Marsolin on 2007-01-15
[KBasic]("http://linuxappfinder.com/package/kbasic") is a free BASIC IDE for Linux.

---

### Post by ardchoille42 on 2007-01-15
Gambas is free and it's in the repos.

---

### Post by Adramelech on 2007-01-15
Maybe this can work for you [http://www.freebasic.net/index.php/about]("http://www.freebasic.net/index.php/about")

---

### Post by Coop on 2007-01-16
Hello
I downloaded and installed gamba from the repositories,but where do I type the "10=something" stuff?
When I did BASIC in class 6,I did it by typing commands like this:```
10 let something = something
``` in a command line like interface.
Please tell me how to use gambas.
Also I'll try KBasic and freebasic.
Please reply to me.
Ahmed

---

### Post by Matt Nichols on 2007-01-19
The standard version of REALbasic is free for Linux, but I have a hunch that this is because it is not fully supported on this platform yet. If you want to try it out, download RB for Linux and select the first option on the install, I think it indicates that it is free here. The REALbasic syntax is similar to that of BASIC, though I don't think it is identical. It might be worth trying out.

---

### Post by lothar_m on 2007-01-19
> **Coop said:**
> Hello
I downloaded and installed gamba from the repositories,but where do I type the "10=something" stuff?
When I did BASIC in class 6,I did it by typing commands like this:```
10 let something = something
``` in a command line like interface.

Ahmed

the use of numbers in the beginning of lines is no longer necessary....  the language as evolved from the 80's spectrum computer.

As i recall the let command has also been dumped

old way: ```
let variable1 = value
```

"new way" ```
variable1 = value
```

---

### Post by geakMonkey on 2007-03-12
I have been researching BASIC for a MS Windows project. I tried the RealBASIC and really did not like it. I tried it on XP. Here is a list online: [http://basic.mindteq.com/LinuxList.asp]("http://basic.mindteq.com/LinuxList.asp")

I would be interested in continuing topics on learning and using BASIC for Linux.

---

### Post by musingattheruins on 2007-09-20
FreeBasic is the best basic that I have ever seen.  (No I do not work for the project.)  It is as close to C++ that Basic can get.  It is as close to GWBASIC (well, Quick Basic) that a Basic compiler has been in a while.

You can take something like:

10 Let something% = 10
20 PRINT something%

and compile it (with -lang qb) and get an independent executable file.
You can then take this code and compile it on Windows and get an executable file there, too.  (14KB)

Once your bored there you can do something like:

Type something
   mystuff as integer = 1
   declare sub TestIt()
End Type

Sub TestIt()
  Print mystuff
End Sub

' Main code
Dim myvar as something
myvar.mystuff = 10
myvar.TestIt()

If you don't get the implication of the second set of code take my word for it, it's big.  It's the reason you will probably not need to leave FreeBasic for a better compiler.  

Good luck!

(You need the 0.18x version of the compiler to do the class-like oop stuff. There's no Ubuntu package for it but the install from [http://www.freebasic.net](http://www.freebasic.net) for Linux works on Unbuntu.)

---

### Post by Matt Nichols on 2007-09-20
Thanks for the info and mini-tutorial. A while ago I gave up on attempting to continue to use something BASICish for Linux, and switched over to Python (+GTK & Glade). I am enjoying it quite a bit, and suggest it if you want something new.

---

