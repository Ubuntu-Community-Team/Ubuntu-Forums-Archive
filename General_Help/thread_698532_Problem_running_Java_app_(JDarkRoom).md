---
title: "Problem running Java app (JDarkRoom)"
date: 2008-02-16
forum: General Help
---

### Post by ffahog on 2008-02-16
I'm trying to download and install / run the newest version of JDarkRoom, which is a program that I loved to use back when I was running XP.

The download file from the official website is a JAR file. When I double-click on it, Ubuntu opens it up using the archive manager. When I right click on the file and choose "Open with 'Sun Java 6 Runtime'" nothing happens. When I open a terminal and write:

```
java -jar JDarkRoom.jar
```

It tells me: "Unable to access jarfile JDarkRoom.jar"

I get similar results after I extract JDarkRoom into a directory and try to open / run it.


Can anyone help me get the program up and running?

---

### Post by luisromangz on 2008-02-16
When you run it from the command line, are you in the same folder that the jar file is?

---

### Post by Shippou on 2008-02-16
I think first get the latest version of java:

```

sudo apt-get install sun-java6-jdk

```

hope this helps.

---

### Post by Shippou on 2008-02-16
I know this is double posting, but then I'm not spamming this forums. I have difficulty in using the quick reply and edit options.

Where do you get JDarkRoom? I want to try it... :)

---

### Post by ffahog on 2008-02-16
[http://www.codealchemists.com/jdarkroom/](http://www.codealchemists.com/jdarkroom/)


Thanks for the help. I'm pretty sure I've got the most recent version. (Yes, I'm in the same folder). Unfortunately, I have to go right now, but I will be back later and resurrect this thread with my results.

Do other people have no problems running it?

---

### Post by Shippou on 2008-02-18
Hello there... 

Just trying to run JDarkRoom....

Here are the results in the command prompt: 

```

shippou@JKQXZ:~/Desktop$ java -jar JDarkRoom.jar /My JDarkRoom Files/writing.txt
Starting JDarkRoom with '/My JDarkRoom Files/writing.txt' ...
Full-screen mode not supported.  Please consider upgrading your version of Java, or using JDarkRoom on a device that supports full-screen mode.
Thank you for using JDarkRoom.  Have a nice evening!
shippou@JKQXZ:~/Desktop$

```

Doesn't run what is intended.... :lol:

---

### Post by ffahog on 2008-02-18
Shippou,

Go into your JDarkRoom directory, into the 'config' directory, and the properties text file. Find the line that says 'force full screen', and make that it reads 'true' instead of 'false'.

By the way, it turns out I **was** in the wrong directory. Ugh! Thanks for the help everyone, I've got the program running now!

---

### Post by Shippou on 2008-02-19
Finally made it work...

I pasted the jar file at my Desktop. Then when I ran it in terminal it made a folder named "conf."

I visited JDarkRoom's site where it says modify the config file.
Edited the folder at my Desktop; still didn't work.

When I edited it in my home directory, it worked.

It's first time I encountered the app.... it is literally a  Dark Room.... :)

Thanks for the app... It's really great! :) They programmed it nicely... Maybe using JFileChooser in saving files.... :)

--> Weird thing: The app does not work when the jar file is extracted and its main class file is run....

---

