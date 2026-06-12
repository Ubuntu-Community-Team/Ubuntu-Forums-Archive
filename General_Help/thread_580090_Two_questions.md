---
title: "Two questions"
date: 2007-10-18
forum: General Help
---

### Post by gamelord12 on 2007-10-18
I plan on getting a Dell laptop, but to really be a show-off, I'd like to use as much eye candy as possible.  Will the integrated graphics card on the Ubuntu-configured Dell laptop be able to handle Compiz-Fusion or Beryl in all their glory?  My Virtual Box certainly can't.  Also (and I consider this the same question), how pretty does GNOME get?  If it doesn't have those transparent window-esque things, I might stick to KDE because I like pretty things.

Second question...I know I don't need to do things this way, but I'm in a Computer Science class that programs in Java.  We have to download Java and add it to our system's class path or whatever that is.  I followed the directions word-for-word on Windows, and it works just fine, but I didn't understand what it was that I was doing (and that's rare for me).  I tried to install it on my Ubuntu virtual machine following his directions, but they were a lot more vague:

"Installing Java on your home computer
We use Java 1.5 in CS111.

Windows:

   1. Go to Sun's download page, download and install the "JDK 5.0 Update 12" (third download button from the top). You do not need to download the version that includes NetBeans (though you may do so if you wish). Update 12 is the most recent version as of Sept 4, but any later version is also ok.
   2. Add Java to your system PATH:
         1. Open the Start Menu.
         2. Right click on "My Computer" and choose "Properties".
         3. Click the "Advanced" tab.
         4. Click the "Environment Variables" button.
         5. In the lower table ("System variables"), select the variable "Path" and press Edit.
         6. To the end of the variable value, add a semicolon and then the following:

            C:\Program Files\Java\jdk1.5.0_12\bin

            Don't replace the entire existing value. The "_12" part above refers to Update 12. If you download a later update, replace the "_12" with the appropriate number. 
   3. Configure your CLASSPATH:
         1. Open the Start Menu.
         2. Right click on "My Computer" and choose "Properties".
         3. Click the "Advanced" tab.
         4. Click the "Environment Variables" button.
         5. In the lower table ("System variables"), select the variable "CLASSPATH" and press Edit. If you don't see a variable with that name, stop here - you don't need to set your CLASSPATH.
         6. To the end of the variable value, add a semicolon and then a period. Don't replace the entire existing value. 
   4. Compile and run your programs from Command Prompt. 

Note that the installation of some software (notably the QuickTime media player) will alter your CLASSPATH and cause problems using Java. If this happens, follow the procedure given above for configuring your CLASSPATH.

Mac OS X 10.4:
Java 1.5 is built into your operating system.

Mac OS X 10.3:
Java 1.4 is built into your operating system. We use some Java 1.5 features in this course - for those assignments you may need to work in one of the campus Mac labs.

Linux:

   1. Go to Sun's download page, download and install the "JDK 5.0 Update 12" (third download button from the top). You do not need to download the version that includes NetBeans (though you may do so if you wish). Update 12 is the most recent version as of Sept 4, but any later version is also ok.
   2. Add Java to your system path in the startup file appropriate for your shell (.login, .cshrc, .bashrc, etc.).
   3. If necessary, add the current directory (.) to your CLASSPATH environment variable. 

Other platforms:
Talk to a member of the course staff."

While I got Java working by installing it through Synaptic, I feel like I should be able to install it using those instructions.  How do I add Java to my "system path" (what is that?) in the startup file appropriate for my shell (what is my shell and where is that startup file?)?  What is my CLASSPATH environment variable?

---

### Post by kebes on 2007-10-18
> **gamelord12 said:**
> Will the integrated graphics card on the Ubuntu-configured Dell laptop be able to handle Compiz-Fusion or Beryl in all their glory?
I'm not sure. These threads seem to indicate that compiz will work:
[http://www.phoronix.com/forums/showthread.php?t=3137](http://www.phoronix.com/forums/showthread.php?t=3137)
[http://ubuntuforums.org/showthread.php?t=577469&highlight=dell+compiz](http://ubuntuforums.org/showthread.php?t=577469&highlight=dell+compiz)

Hopefully someone who has a Dell laptop can comment on how well Compiz is running. What exact model were you planning on getting?


> how pretty does GNOME get?  If it doesn't have those transparent window-esque things, I might stick to KDE because I like pretty things.
I prefer KDE over GNOME, but both can be configured to make them more "pretty." Check out these sites for wallpapers, skins, and ideas on how to streamline the look of your Linux desktop:
[http://www.gnome-look.org/](http://www.gnome-look.org/)
[http://www.kde-look.org/](http://www.kde-look.org/)

> While I got Java working by installing it through Synaptic, I feel like I should be able to install it using those instructions.  How do I add Java to my "system path" (what is that?) in the startup file appropriate for my shell (what is my shell and where is that startup file?)?  What is my CLASSPATH environment variable?
With a Synaptic install of Java, it should be in your system path, which means that you can invoke it from any command-line (a.k.a. shell, a.k.a. terminal). To check, just [open up a terminal]("http://www.psychocats.net/ubuntu/terminal") (select Applications > Accessories > Terminal in GNOME), and type:
```
java
```
This should return a listing of java options (if it returns "command not found" then this means java isn't installed or needs to be added to your system path).

As for the CLASSPATH issue, [this link should help]("http://java.sun.com/j2se/1.4.2/docs/tooldocs/solaris/classpath.html"). Basically this path is what Java uses to determine where class files will be found during compiling. As the link explains, you can either use the -classpath option on your java command when compiling, or you can use the Linux command "setenv" to define globally what CLASSPATH should be.


Hope that helps.

---

### Post by Tom Mann on 2007-10-18
Why not consider a ubuntu-installed dell laptop?

[www.dell.co.uk/ubuntu]("www.dell.co.uk/ubuntu")

---

### Post by gamelord12 on 2007-10-18
> **Tom Mann said:**
> Why not consider a ubuntu-installed dell laptop?

[www.dell.co.uk/ubuntu]("www.dell.co.uk/ubuntu")

I am.  See the second sentence of my first post.  However, I'm American, so I doubt that link is for me.  I already know where to shop for Ubuntu on the American Dell site, but it's just that I'm going to have to wait until Christmas to get it.  I just wanted to know how the performance on graphics-intensive applications like Compiz-fusion is in case I decide to get one initially configured with Windows that has a better graphics card (Dell only offers one laptop model with Ubuntu) and then overwrite it with Ubuntu afterward.  The advantage of getting the pre-configured laptop is that I KNOW everything will work out of the box.  The last thing I want to do is buy a laptop only to find out that the wireless card isn't supported in Linux.

---

