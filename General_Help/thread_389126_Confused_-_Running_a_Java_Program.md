---
title: "Confused - Running a Java Program"
date: 2007-03-20
forum: General Help
---

### Post by Scunizi on 2007-03-20
I'm trying to run a PDF annotation program written in Java.  The site shows some command line arguements to run the program but I'm confused.  The downloaded zip file contains two folders, one with a lot of .class files and another with a .MF file.  

Do I just place these folders in my ~ directory and run the command lines from there?  Do I have to compile this and install?  This is my first time dealing directly with a java program.  You can see it here [http://www.dklevine.com/general/software/tc1000/jarnal.htm](http://www.dklevine.com/general/software/tc1000/jarnal.htm).

I'm interested in this because it may be a decent replacement for a windows program called J2 Messenger or eFax messenger.  Something I've been searching for for some time.

---

### Post by Jovaro on 2007-03-20
The class files contain the actual program, so just put them anywhere and then run the program from there with the lines that are on the website.

That should do the trick, no compiling or installing is necessary. (class files are what you get when compiling java)

---

### Post by kaamos on 2007-03-20
You've probably just extracted too many files. From the page you linked to:
> 
Either download jarnal.jar, or, for basic PDF support, download jarnal-install.zip and unzip. In either case, to use execute the command java -jar jarnal.jar [options] [file_to_open].


---

