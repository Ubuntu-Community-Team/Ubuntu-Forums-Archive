---
title: "java install"
date: 2007-12-03
forum: General Help
---

### Post by gorlando on 2007-12-03
anyone on this forum help with the below that is unresolved?


[http://ubuntuforums.org/showthread.php?t=629767](http://ubuntuforums.org/showthread.php?t=629767)

---

### Post by erfahren on 2007-12-03
in the terminal do:
```

java -version

```
to see what java version is configured to use by the system, it should be something like:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

If not do:
```

sudo update-alternatives --config java

```
you should see something like:
```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```
--- select the "java-6-sun" one (yours should be the "update 3" one - mine's older)

see if that helps

---

### Post by gorlando on 2007-12-03
i executed the commands 
still not working



[http://game1.pogo.com/error/java-problem.jsp?site=pogo](http://game1.pogo.com/error/java-problem.jsp?site=pogo)

The following error has occurred:
Java Not Found or Not Working

Explanation:
This error means Java (one of the technologies built into most browsers) is not working correctly on your browser.

You must have Java installed on your computer in order to run Pogo games, and it must be functioning properly. Either you don't have Java installed yet, or the Web browser you're currently using doesn't support Java or you have Java (or Javascript) disabled in your browser.

How to Fix the Problem:
Java is a free download that is required to play Pogo games. Not all computers come with Java pre-installed.

If you haven't played Pogo games before and are getting this error, you probably just need to install Java on your computer.
For instructions on installing Java for your operating system and browser click here.

If you believe Java might be installed but disabled for your browser, please be sure to enable the plugin for your browser. If you need help, click here.

If you already have Java installed and it is not disabled, your Java may be out-of-date or is no longer working. In that case, your Java might need to be upgraded or reinstalled. If you need help, click here.


then i went to verify java version, that was fine before, now it is not?...


Verifying Java Version

Oops! You don't have the recommended Java installed.
Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.  

NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation.

---

### Post by erfahren on 2007-12-03
well, ok... if you go back to java.com to verify it should say that you have the correct version now. 

but that pogo site isn't working for me either, in Opera or in Firefox

I clicked where it says:
"If you already have Java installed and it is not disabled, your Java may be out-of-date or is no longer working. In that case, your Java might need to be upgraded or reinstalled. If you need help, click here."

it didn't help much. If you search their FAQs for "java version" (or "java help") you should come up with one that mentions some different games to test. (The links for the pages I found were way too long, I didn't want to mess with posting them here).



One of those FAQ pages said this:
> 
Below, you should see a Java Applet with Java, Browser, and Operating System version information. Follow the instructions below to provide this information to us so that we can better assist you with the problems you may be encountering.
Highlight all 3 lines of text in the information box. 
To highlight the text, left-click before the first letter and continue to hold the mouse button down and drag the cursor to the last character of the third line.
Sometimes, you can right-click in the box and choose Select All.
Copy the text (Ctrl + C) (for Mac users: 'Apple' key + 'C ' key). 
To copy the text, hold down the 'Ctrl' key and the 'C' key down at the same time and this will put the highlighted text into the clipboard memory.
Sometimes, after the text is highlighted, you can right-click and choose Copy.
Paste the text into the Response Field or the Question Field (Ctrl + V) (for Mac users: 'Apple' key + 'S ' key) 
To paste the text, go the text field where you would like the text to appear, usually the Question or Response field. Next, hold down the 'Ctrl' key and the 'V' key at the same time.
Sometimes, you can right-click and choose Paste to put the text into the desired field.


In the box there I got:
```

Java 1.6.0 (Sun Microsystems Inc.) 
Linux 2.6.20-16-generic (i386)
Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; InfoPath.1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)

```
It appears that they're not very "Linux friendly" (or Firefox friendly, maybe). Were you able to access their site with Firefox on Windows?

---

### Post by gorlando on 2007-12-03
thanks for your help.

the only reason i'm trying to get this to work is for a client i installed ubuntu for, otherwise i wouldn't care.

>Were you able to access their site with Firefox on Windows?

i never went on the site myself when i had windows.

the client that wants the pogo site was using aol and windows 98 from what i recall.

gary

---

