---
title: "I need to setup javac"
date: 2006-11-09
forum: General Help
---

### Post by thecynicality on 2006-11-09
I really need to set up a java compiler really fast because i have an assignment due at 5. I downloaded the jdk 5 bin for linux, and i ran the bin but i don't know how to do the javac command on linux i only knew how to do it on windows, can someone help me set this up? Thanks.
Edit/Delete Message

---

### Post by mark2741 on 2006-11-09
Too late now I guess, but if you're still looking to get the java compiler going on ubuntu then the easiest way is to use Automatix to install the jdk 1.5. It gets installed and configured properly very easily that way.

Then you only need to open up a terminal and type:

javac myClass.java

(replace myClass.java with name of the class you want to compile)

If you run into 'symbol not found' errors or anything else then check your classpath. To do so:

echo $CLASSPATH

It can have anything in there so long as the last thing in there is a semicolon. Most likely all you need is to set your classpath to the current directory, by doing this:

export CLASSPATH=;

The semicolon just tells the jdk to look in the current directory for your class files, in addition to the java home directory.

> **thecynicality said:**
> I really need to set up a java compiler really fast because i have an assignment due at 5. I downloaded the jdk 5 bin for linux, and i ran the bin but i don't know how to do the javac command on linux i only knew how to do it on windows, can someone help me set this up? Thanks.
Edit/Delete Message

---

