---
title: "open up a c++ compiler?"
date: 2005-10-11
forum: General Help
---

### Post by websurrfr on 2005-10-11
Is there a c++ compiler built into ubuntu?  (running 5.10) I tried to run python but it's all command line, i would think that would be very difficult to program since you can use your mouse to up and down your code and click around.  Is there a way to open python in a window like this or another compiler anyone reccomends?  Thanks.

---

### Post by swerner on 2005-10-11
[QUOTE=websurrfr]Is there a c++ compiler built into ubuntu?  (running 5.10) I tried to run python but it's all command line, i would think that would be very difficult to program since you can use your mouse to up and down your code and click around.  Is there a way to open python in a window like this or another compiler anyone reccomends?  Thanks.[/QUOTE]

Hello websurrfr, welcome to the world of programming in Linux.  Yes there is a C++ compiler built into Ubuntu, and it's a very good one, it's called gcc (GNU Compiler Collection, it actually compiles more than just C++).  However, gcc by it's self is all command line stuff, and you want to keep away from that... for now ;).  

What it seems you want is an IDE (Integrated Development Environment), these are available for both Python and C++.  An IDE allows you to write your code, compile it and debug it all in one friendly interface.  I have not used one IDE that handels both C++ and Python successfully.  I tend to use seperate IDE's for that.  And with Ubuntu it's easy to install a whole range of IDE's, here I will only discuss 3 of them, a C++ IDE called Anjuta, a Java IDE called Eclipse, and Eric the Python IDE.   You can simply download and install any of these IDE's, just click on "Applications > Add Applications > Programming environments" and click on the expand link.  Here check the "Devhelp" and "Glade Interface Designer" check boxes.  Then click on the next expand "More programs ..." object. Here you select the above IDE's I mentioned (Anjuta, Eclipse and Eric) and click install, go and have a cup of coffee, or soy latte.  Once installed these programs will be available under "Applications > Programming"

About the IDE's (read the blurb in the "Add Applications" program):
Anjuta is a great C++ IDE for Gnome, it will simply allow you to create new applications, either command line based or graphical.  It will allow you to easily build (compile) your package and quickly make it into a distributable source package.

Eclipse is an excellent (that's probably an understatement) IDE available for Linux and Windows, it is written in Java and originally made for Java.  Essentially it is the most comprehensive programming environments available.  Although the learning curve can be high to make use of all it's feature, it still provides an excellent starting point for programming.  I know it supports C and C++, but I heard that the support is still limited at the time (that was about a year ago though).  And I do know that many professionals use this as their C++ development tool.  You can enjoy your coffee, or soy latte while viewing some of Eclipse's animated tutorials.

Eric, I haven't used much, but have heard lots about.  It will definately be more friendly than your command line application you saw.  Although I do love the command line for writing some quick and dirty code ;).

I wish you all the best for programming in Linux, there are lots of tutorials available on the net, just ask if you need some good links.  Each IDE comes with it's own documentation as well, although this is generally about the IDE itself, and it's not a programming language reference.

---

### Post by darkmatter on 2005-10-11
For Python, you could try [DrPython](http://www.gnomefiles.org/app.php?soft_id=465) or [Culebra-IDE](http://www.gnomefiles.org/app.php?soft_id=764)

---

### Post by websurrfr on 2005-10-11
ahh, many many thanks for all the advice, and IDE is the word I was looking for!

---

