---
title: "[SOLVED] how to install and use java compilers?"
date: 2008-01-06
forum: General Help
---

### Post by crazyfuturamanoob on 2008-01-06
I am new to java (and linux too). How can I compile .java to .jar? 
How can I use/install java compilers? I got ubuntu gutsy gibbon.

---

### Post by luisromangz on 2008-01-06
You don't compile .java to .jar. A .jar file is just a bunch of .class files (which is the result of compiling .java files) zipped, and which some extra files that tells the JVM which class contains the entry point for the application and other info.

About using/installing, well, you should install Sun's Java SDK from the repositories, if you can't see them, enable the universe/multiverse repositories.

And get a good Java book, you are going to need it.

---

### Post by crazyfuturamanoob on 2008-01-07
So can my cellphone run .java files? I think you misunderstood my problem.
I want to run .java file, just like any other program. And about installing java tools,
do I need to somehow "configure" the tools, or is it enough that I just install them?
I already tried to install them, but I saw only useless .jar .exe .zip .crap files, and 
I couldn't run any of them (exes weren't working either).

---

### Post by heindsight on 2008-01-07
.java files are java source files. To get something that can be executed, you need to use the
```
javac
``` command (from the Java SDK) to compile your java source code into a collection of java .class files. The program can then be executed using the ```
java
``` command. If you want an executable .jar file, you need to use the ```
jar
``` command.

Have a look at the manuals for these commands for detailed information on how to use them.

As luisromangz said, you need to install the Sun Java SDK from the repositories.

---

### Post by crazyfuturamanoob on 2008-01-07
But where do I type those commands? Terminal?

---

### Post by crazyfuturamanoob on 2008-01-10
Well, I just downloaded and installed those with synaptic:
> sun-java6-bin
sun-java6-demo
sun-java6-jdk
sun-java6-jre
sun-java6-source
Now, how do I use them?
I have a simple helloworldapp, HelloWorld.java.
I went to the folder HelloWorld.java is located, and typed 
```
javac HelloWorld.java
```
Something happened (console window appeared and then disappeared),
but HelloWorld.java is exactly same than before. Where is the compiled one?
And did I put the "javac" thing even to right place?

---

### Post by heindsight on 2008-01-10
try it in a terminal

---

### Post by crazyfuturamanoob on 2008-01-10
Well, I did it by the following way:
1. I opened the correct location with the default graphical file browser.
2. I pressed Alt+F2 and checked the "run in terminal" box
3. I typed the code there and ran it.
I am new to ubuntu, and I don't know, 
how to go to a certain directory with console,
could someone tell me how?

---

### Post by crazyfuturamanoob on 2008-01-13
I can't find the compiled file (I looked only the directory, where the source file is).
Where does "javac" create the compiled file? Help!

---

### Post by crazyfuturamanoob on 2008-01-13
This is still unsolved. My problem is:
I don't know where java compilers create the compiled files.
Just tell me the directory. Thanks
Edit: 
Wait, I just seached my system with the default tool, and found nothing.
I tried to compile with "javac HelloWorld.java". Should I enter a directory too?

---

### Post by heindsight on 2008-01-13
From the javac man page:
>  By  default, the compiler puts each class file in the same directory as its source file. You can specify a separate destination directory with -d 


To compile HelloWorld.java you can either enter the command
```
javac HelloWorld.java
``` in a terminal, in the same directory where HelloWorld.java is located, or you can run ```
javac /full/path//to/HelloWorld.java
``` from any directory.

If you don't know how to find your way around with at the command line, I suggest you have a google for some bash command line tutorials.
If you're really not comfortable doing things from a terminal, you might want to have a look at the Eclipse IDE (which is available in the repos).

---

### Post by SyL on 2008-01-13
When you compile a .java file you get a .class compiled java code.

If you run javac MyClass.java
You will get MyClass.class on the same directory 

```

syl@Oniris:~$ javac tmp/Item.java 
syl@Oniris:~$ ls -lsa tmp/Item.*
4 -rw-r--r-- 1 syl syl 724 2008-01-13 20:12 tmp/Item.class
4 -rwx------ 1 syl syl 401 2008-01-13 20:06 tmp/Item.java

```


If you want to specify the directory where the class file will be stored, then use the -d option. The class file will be then write to the directory you specified + all the package arborescence:

 ```

syl@Oniris:~$ javac -d tmp/aa tmp/Item.java
syl@Oniris:~$ ls -lsa tmp/aa/net/roidagaubert/ft/frontend/bean/items/


----------------------------------------------------------------------------------
syl@Oniris:~$ more tmp/Item.java

package net.roidagaubert.ft.frontend.bean.items;

public class Item {
...

```



But as heindsight, if you want to develop something you should use eclipse.

---

### Post by alas on 2008-01-28
yeap, but if eclipse is too fat for you just install sun's wireless toolkit, it's everything you need except a text editor with java syntax highlight support, I use it to make my little programs for my cell phone, and sometimes compile some 3rd party programs, in 3 steps, create new project, add/make the *.java, hit build button and voila! a *.jar to put in my phone ;)

Atentamente [email]Alastors_@_gmail.com[/email]

edit: swtk creates a tree for your proyect, */src/ is where you put the *.java and */bin/ is where you find the *.jar

---

