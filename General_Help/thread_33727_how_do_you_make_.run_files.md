---
title: "how do you make .run files"
date: 2005-05-11
forum: General Help
---

### Post by DarkGreen16 on 2005-05-11
I did a brief google search but don't really know what to search for. Every search I do comes up with stuff about make so I'm trying to get a more simple and straight forward answer by asking here.

So basically how do I make a .run file that will basically serve as a package that runs a script inside the package?

Like if I had a directory with 6 or so files in it as well as more directories and a script to install it like x.sh how would i package that up as installx86.run so when someone does a ./installx86.run it would execute the x.sh script inside the package and install properly?

Hope that makes sense.

---

### Post by tread on 2005-05-12
Is [autopackage](http://autopackage.org/) what you are looking for?

---

### Post by rykel on 2005-05-12
[QUOTE=tread]Is [autopackage](http://autopackage.org/) what you are looking for?[/QUOTE]
 I agree 100% with Autopackage! It is the best thing to happen in my Linux experience after Linux itself.     =)

---

### Post by DarkGreen16 on 2005-05-12
thx for the reply but I don't even have a .package

all i have is the necessary files to install in a folder with an install script....no .package

besides im trying to make a .run not a .package

---

### Post by mhearn on 2005-05-12
[QUOTE=DarkGreen16]thx for the reply but I don't even have a .package

all i have is the necessary files to install in a folder with an install script....no .package

besides im trying to make a .run not a .package[/QUOTE]
 You want a program called "makeself", that is what produces the .run files.

---

### Post by DarkGreen16 on 2005-05-13
thanks mhearn that is exactly what I was looking for...

---

