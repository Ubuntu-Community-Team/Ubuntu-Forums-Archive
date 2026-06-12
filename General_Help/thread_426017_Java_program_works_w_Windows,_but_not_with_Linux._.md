---
title: "Java program works w/ Windows, but not with Linux. How to use with WINE?"
date: 2007-04-28
forum: General Help
---

### Post by enthusaroo on 2007-04-28
Hey everyone,

I made the switch from Windows to Ubuntu Linux about a week ago with the release of 7.04.

There is one Java application that works under Windows which I would really like to have work under Linux.

First off, I installed Sun's Java for Linux already, so I can use Java with Firefox. However, when I try running this particular Java application (the one that works under Windows) it won't run under Linux. I also have WINE installed. I can run some Windows applications under WINE. However, I do not know how to run the Windows version of Java. That's what I need to do. I need to be able to run the Windows version of Java, so I can get this Windows based Java application to work. 

Looking for help please. I really don't want to go back to Windows just because I can't get this one application to run under Linux. :(

If you're wondering what the Java application is, it's called the Search Guide Application that ChaCha.com search guides use to help guide people on searches. I work part time for ChaCha as a search guide. On ChaCha's web site it says they are working on a Linux version of their Java software, but who knows how long that will take... 2 weeks... 1 year? It's very unclear. That's why I really need to find a way to get it to work now under Linux. I would link to the application, but you have to be logged into ChaCha as a search guide in order to view / download it. :(

---

### Post by robbydek on 2007-04-28
Can you see Java sites on your Linux Firefox?  Or if you can what is your reason for what Java for Windows on Linux?

---

### Post by enthusaroo on 2007-04-28
> **robbydek said:**
> Can you see Java sites on your Linux Firefox?  Or if you can what is your reason for what Java for Windows on Linux?

Yes, as I said, there's no problems using Java in Firefox. 

Here is the reason why I need to get this Java application to work in Linux:

> 
If you're wondering what the Java application is, it's called the Search Guide Application that ChaCha.com search guides use to help guide people on searches. I work part time for ChaCha as a search guide. On ChaCha's web site it says they are working on a Linux version of their Java software, but who knows how long that will take... 2 weeks... 1 year? It's very unclear. That's why I really need to find a way to get it to work now under Linux. I would link to the application, but you have to be logged into ChaCha as a search guide in order to view / download it. 

Basically, it's a Java application that runs under Windows. In Windows, I simply double-click on the application and it works. I have Java installed under Ubuntu, but when I try to double-click on the same Java application absolutely nothing happens. That's why I want to know how I can make it run under Linux.

---

### Post by robbydek on 2007-04-28
What type of plugin is it?  If it's a dll file, you'll have to find another program to run it in.  Personally Linux is good, but it lacks things that I need, which is why I have a dual boot system with Windows Vista.

---

### Post by enthusaroo on 2007-04-28
> **robbydek said:**
> What type of plugin is it?  If it's a dll file, you'll have to find another program to run it in.  Personally Linux is good, but it lacks things that I need, which is why I have a dual boot system with Windows Vista.

It's not a plugin.

The Java application I am referring to is just a ".JS" file. 

> **robbydek said:**
> Personally Linux is good, but it lacks things that I need, which is why I have a dual boot system with Windows Vista.

I know, actually my system is dual-boot too with Windows XP. I'm just trying to shift entirely to Ubuntu and give up Windows. For the last week I've been almost all of my work and Internet usage in Ubuntu, which is why I really want to get this one to work.

---

### Post by Lord Illidan on 2007-04-28
If you start it from the terminal with java <insert command name> does it work?

---

### Post by robbydek on 2007-04-28
I wish I could help you more but I'm not that familiar which .js files.

---

### Post by enthusaroo on 2007-04-28
> **robbydek said:**
> I wish I could help you more but I'm not that familiar which .js files.

Oh! My mistake! It's actually a ".jnlp" file. Not a ".js" as I originally thought. I'm not sure if that makes any difference. :p

Normally this file runs in Java under Windows. 

> **Lord Illidan said:**
> If you start it from the terminal with java <insert command name> does it work?

I typed: ```
java main.jnlp
``` but it gave me the following error in Terminal:
```
Exception in thread "main" java.lang.NoClassDefFoundError: main/jnlp
```

:(

---

### Post by aldenhg on 2007-04-28
.jnlp files are Java Network Launch Protocal files. I'm no expert, but I think that they are more or less link files that should tell Java where to find .jar files. While I may be talking out of my ***, I think you probably need to make sure you A: have all the files associated with the program with their directory structure intact and B: a live internet connection. Since you're posting here, i'm guessing that B is already taken care of.

---

### Post by enthusaroo on 2007-04-28
Actually, this guy was having the exact same issue as me in October, 2006, but unfortunately there's no solution posted: [http://ubuntuforums.org/showthread.php?t=275316](http://ubuntuforums.org/showthread.php?t=275316)

---

### Post by kalpik on 2007-04-28
AFAIK, if its purely java, it should work on linux too.. Cuz java code executes in a Java Virtual Machine.. Which is same on every platform, that's the whole point behind java!

---

### Post by Lord Illidan on 2007-04-28
But if it is using windows libraries, then I don't think it will work..

---

### Post by yesudeep on 2007-05-20
Hello there,

JNLP files are XML files used by Java to launch Java Web Start applications.  You can run Java Web Start applications on Linux.  All you need to do is.

To run it from **Firefox**

[LIST=1]
[*] Try opening a JNLP (*.jnlp) file with Firefox, for example.
[*] When Firefox prompts you to either Open or Save the file, choose Open.
[*] Browse for a program called `javaws` located in the `bin` directory of your Java installation. For example, I installed the Java Runtime environment at `/usr/java/jre1.6.0`.  Therefore, my local copy of `javaws` is located in the directory called `/usr/java/jre1.6.0/bin`.  This program, called Java Web Start, needs to be associated with the MIME type for JNLP files in Firefox.
[/LIST]

**To run a Java Web Start application directly** you can instead *open a terminal and type*

```

/usr/java/jre1.6.0/javaws example.jnlp

```

Alternatively, if the Java `bin` directory is in your PATH environment variable (echo $PATH)

```

javaws example.jnlp

```

You can also configure it to run when you **double click** it by right clicking on the file and choosing the `javaws` program from the **Open With...** dialog.  This will associate this type with the appropriate program in Nautilus, for instance.

In general, newcomers to Linux (especially those with prior experience using Windows) take time figure out solutions.  Please avoid buying into arguments that claim Linux cannot do this or that without researching that particular statement.   

As a side note, .js files are generally JavaScript script source files.  However, nothing stops you from naming an image extension to js, except that it will make it more difficult for programs to determine the type of that file and may in turn corrupt that file.

Hopefully, this solves your problem.  Good luck.

Regards,
Yesudeep.

---

