---
title: "Java on UBUNTU?"
date: 2007-05-17
forum: General Help
---

### Post by xavier_r on 2007-05-17
I can access this site [http://charting.bseindia.com](http://charting.bseindia.com) from windows without a problem
Its a Java applet to see stocks

Also in windows using appletviewer I can run the applet
C:\> appletviewer [http://charting.bseindia.com](http://charting.bseindia.com)

While in UBUNTU neither can i access the site nor the applet runs properly
It only loads partially and then breaks
Even though java is installed and java plugins are enabled

While running appletviewer in UBUNTU I get this problem 
[B]
java.lang.NullPointerException
        at equis.metastock.MS4Java.repaint([DashoPro-V1.2-120198])
        at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:95)
        at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
        at java.awt.Component.setBackground(Component.java:1575)
        at equis.metastock.MS4Java.init([DashoPro-V1.2-120198])
        at sun.applet.AppletPanel.run(AppletPanel.java:417)
        at java.lang.Thread.run(Thread.java:619)[/B]

Please help me run this applet on ubuntu[B]
It is one of the reasons why i still have to use windows[/B]

Thanks
Xavier

---

### Post by nereid on 2007-05-18
Which version of java do you use?

EDIT: And it is possible to write something in Java which is platform dependent.

---

### Post by bukwirm on 2007-05-18
Try installing the Sun version of java, if it's not already installed. (the package is called sun-java5-jre)
Then run "sudo update-alternatives --config java" and choose the sun version.

---

### Post by ShirishAg75 on 2007-05-18
I was able to see all the stocks & stuff using GNU classpath without an issue. It just renders things a bit slow as its an interpretor. I have installed gcj-compat-java as well as gcj-compat-java-dev alongwith couple of other things.

---

### Post by xavier_r on 2007-05-18
> Which version of java do you use?

On windows its sun java 5.
On ubuntu i have tried sun java 5 as well as 6.

---

### Post by xavier_r on 2007-05-18
> **ShirishAg75 said:**
> I was able to see all the stocks & stuff using GNU classpath without an issue. It just renders things a bit slow as its an interpretor. I have installed gcj-compat-java as well as gcj-compat-java-dev alongwith couple of other things.

This is GNU java right?

---

### Post by vikramsharma on 2007-05-18
> **xavier_r said:**
> This is GNU java right?

Yes, you might have to set the path for sun java.  Try java -version in the terminal, if the response is of some gcj version you would have to set path for sun java that you have already installed.

---

### Post by xavier_r on 2007-05-18
> **vikramsharma said:**
> Yes, you might have to set the path for sun java.  Try java -version in the terminal, if the response is of some gcj version you would have to set path for sun java that you have already installed.

Dude those things are set...
Java is perfectly installed on my computer...

I am only wondering why the right applet does not load
the left applet loads perfectly

---

### Post by vikramsharma on 2007-05-18
> **xavier_r said:**
> Dude those things are set...
Java is perfectly installed on my computer...

I am only wondering why the right applet does not load
the left applet loads perfectly

My bad, sorry for jumping the gun there.

---

### Post by xavier_r on 2007-05-19
Can anyone please successfully run this Java app on your ubuntu machine?
[http://charting.bseindia.com](http://charting.bseindia.com)

I cannot see any graph

---

### Post by Extreme Coder on 2007-05-19
even if sun's java is installed, maybe it isn't the default. that's why we're asking you to type java -version ,  so we can see what is the default.

Extreme Coder

---

### Post by nereid on 2007-05-20
I also got the null pointer exception with sun-1.5. So IMHO this seems to be a problem of their MS4 package or something like that. As I pointed out before, it is possible to write non-portable Java applications. Has anybody tried this with an Apple? If Mac OS X also can't handle it, then it is definitely a problem from their package.

---

### Post by xavier_r on 2007-05-20
> **Extreme Coder said:**
> even if sun's java is installed, maybe it isn't the default. that's why we're asking you to type java -version ,  so we can see what is the default.

Extreme Coder

here you go:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

I know its the default, cause i have installed it and made it the default

---

### Post by xavier_r on 2007-05-20
> **nereid said:**
> If Mac OS X also can't handle it, then it is definitely a problem from their package.

Yea Good idea :)

If any Mac users or any other Linux users wanna try it out, 
Please see that [http://charting.bseindia.com](http://charting.bseindia.com) works on your computer and you can see the graph

---

### Post by marmiteOlz on 2007-05-20
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)

thats mine and i tried the link to bseindis.com and all i saw was  "click here to download plugin"
but i got no applets unlike u had 1
i installed from java.com itself AND using getautomatix
neither worked however installed ok
and before someone says it   i tried them 1 at a time   not installing both.. incase of conflict, power struggle etc..

---

### Post by vikramsharma on 2007-05-21
> **marmiteOlz said:**
> java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)

thats mine and i tried the link to bseindis.com and all i saw was  "click here to download plugin"
but i got no applets unlike u had 1
i installed from java.com itself AND using getautomatix
neither worked however installed ok
and before someone says it   i tried them 1 at a time   not installing both.. incase of conflict, power struggle etc..

The sites are mostly designed with users running Internet Explorer on Windows in mind, so on might have a problem.

---

### Post by xavier_r on 2007-05-21
> **marmiteOlz said:**
> java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)

thats mine and i tried the link to bseindis.com and all i saw was  "click here to download plugin"
but i got no applets unlike u had 1
i installed from java.com itself AND using getautomatix
neither worked however installed ok
and before someone says it   i tried them 1 at a time   not installing both.. incase of conflict, power struggle etc..

did you try using the command 
$ appletviewer [http://charting.bseindia.com](http://charting.bseindia.com)

---

### Post by xavier_r on 2007-05-21
> **vikramsharma said:**
> The sites are mostly designed with users running Internet Explorer on Windows in mind, so on might have a problem.

It runs perfectly well on firefox in Windows...
As well as with appletviewer, again, in Windows only...

Actually its not a site but the URL for an applet ;)

---

### Post by xavier_r on 2007-05-21
> **xavier_r said:**
> 
java.lang.NullPointerException
        at equis.metastock.MS4Java.repaint([**DashoPro**-V1.2-120198])


I did up some searching and came up with this
[http://www.preemptive.com/products/dasho/](http://www.preemptive.com/products/dasho/)

Java Obfuscator, Java Code Protector and Pruner = Dasho Pro

Now with that info anyone knows how to steer clear of that null pointer exception?

---

### Post by vikramsharma on 2007-05-21
> **xavier_r said:**
> It runs perfectly well on firefox in Windows...
As well as with appletviewer, again, in Windows only...

Actually its not a site but the URL for an applet ;)

You could use crossover office on Linux or Wine and install Internet Explorer with Java, maybe that would help.

---

### Post by yesudeep on 2007-05-21
Greetings,

The applet crashed on my Ubuntu box using Firefox 2.x and Opera 9.x.  Refreshing the page in Firefox made it work.  No go yet in Opera though.  I have IE 5.0, 5.5, and 6.0 installed on Linux at the moment but IE will not render the applet due to the lack of a proper JRE plugin.

Here's a screenshot: 

[http://jburd.hopto.org/images/bsechart.png](http://jburd.hopto.org/images/bsechart.png)

Here's my version of Java:

```

**$ java -version**
java version "1.6.0_01"
Java(TM) SE Runtime Environment (build 1.6.0_01-b06)
Java HotSpot(TM) Client VM (build 1.6.0_01-b06, mixed mode, sharing)

**$ which java**
/usr/java/jdk1.6.0_01/bin/java

```

And here's the plugin location for Firefox

```

**~/.mozilla/plugins$ ls**
flashplayer.xpt  libflashplayer.so  **libjavaplugin_oji.so**

```

When you visit the URL  `about : plugins` (sans spaces and quotes) in Firefox, you should see the following:

```

**Java(TM) Plug-in 1.6.0-b105**

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6 	Java 		Yes

```

My JRE is installed here:  
```

/usr/java/jre1.6.0

```

And the plugin for Firefox is located here: 
```

/usr/java/jre1.6.0/plugin/i386/ns7/libjavaplugin_oji.so

```

You will need to copy that file over into:
```

/usr/lib/firefox/plugins/libjavaplugin_oji.so

```

And ~/.mozilla/plugins/libjavaplugin_oji.so is a symlink to the above file.
```

yesudeep@athena:~/.mozilla/plugins$ ls -la
lrwxrwxrwx 1 yesudeep yesudeep      45 2007-02-11 13:08 libjavaplugin_oji.so -> /usr/lib/firefox/plugins/libjavaplugin_oji.so

```

Ok, so if that's already sounding so complicated, don't be hassled.  Just copy over that file into both directories and you should have your Java plugin ready.
Now, from what I gather, you already have your Java plugin configured and one part of the applet working.  What I now need to figure out is why the other does not work.
For that I will need you to show me how you installed Java and configured Firefox.

Regards,
Yesudeep.

---

### Post by xavier_r on 2007-05-24
> **vikramsharma said:**
> You could use crossover office on Linux or Wine and install Internet Explorer with Java, maybe that would help.

Dude its not a site its a java applet URL, it depends on Java, not Internet Explorer or Mozilla...

---

### Post by xavier_r on 2007-05-24
> **yesudeep said:**
> 
The applet crashed on my Ubuntu box using Firefox 2.x and Opera 9.x.  Refreshing the page in Firefox made it work.  No go yet in Opera though.  I have IE 5.0, 5.5, and 6.0 installed on Linux at the moment but IE will not render the applet due to the lack of a proper JRE plugin.

Thanks a lot buddy for your effort, now i at least know that it works... :popcorn:


Here's my version of Java:

```

**$ java -version**
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

**$ which java**
/usr/bin/java

Thats a symbolic link to  /usr/lib/jvm/jdk1.6.0/bin/java

```

My JRE is installed here:  
```

/usr/lib/jvm/jdk1.6.0/jre

```

I tried your plugin method
But it still doesnt work

Have you tried viewing the site using appletviewer?
try giving the command
$ appletviewer [http://charting.bseindia.com](http://charting.bseindia.com)

---

### Post by haskelm on 2007-05-24
No, I can't see it. I also can't play yahoo games because this stupid java doesn't work in Firefox on my Ubuntu machine. I thought this version of linux was supposed to bring Microsoft Windows converts.

> **xavier_r said:**
> Can anyone please successfully run this Java app on your ubuntu machine?
[http://charting.bseindia.com](http://charting.bseindia.com)

I cannot see any graph

---

### Post by yesudeep on 2007-05-27
> **haskelm said:**
> No, I can't see it. I also can't play yahoo games because this stupid java doesn't work in Firefox on my Ubuntu machine. I thought this version of linux was supposed to bring Microsoft Windows converts.

No, it was not supposed to bring in Windows converts only help them ease into the system.  Satisfying every user is every developer's dream, but it is mostly an illusion and more likely to remain a dream because users are never satisfied with software.  They always want more.  Please have some patience.

One plain thing I do not understand about Windows users is why they can't do a bit of reading and playing around?  Using Linux requires some gray matter up there.  Don't give up.  There's always help around, and many people like us don't get paid to help you full-scale, yet we do it.  The reason is very simple.  Windows locks you into a model that it wants you to use and does not let you free yourself; free and open-source operating systems don't.  We want you to be free and productive.  We're an evolving community of professionals and users.  Please help develop and motivate.

The problem you are talking about lies with proprietary software not willing to cooperate with open-source software, and not the other way around.  Software patents and legal restrictions prevent open software from supporting features that would otherwise be trivial to implement.  Java has been proprietary and only now has the JDK been released under the GPL (Sun finally has showed some leadership, intelligence, and courage there).  Oh, and by the way, Microsoft itself does not support Java.  ;)

The point is simple.  Don't like it?  Fix it or don't use it.  Stop cribbing--it's useless. The solution is to find an appropriate solution. :)

Regards,
Yesudeep.

---

### Post by yesudeep on 2007-05-27
Dear op,

The problem obviously lies with the way the applet has been programmed, because standard error output shows a NullPointerException. 

```

java.lang.NullPointerException
        at equis.metastock.MS4Java.repaint([DashoPro-V1.2-120198])
        at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:95)
        at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
        at java.awt.Component.setBackground(Component.java:1575)
        at equis.metastock.MS4Java.init([DashoPro-V1.2-120198])
        at sun.applet.AppletPanel.run(AppletPanel.java:417)
        at java.lang.Thread.run(Thread.java:619)

```

That stack trace should tell you where exactly the problem is.  This issue should be reported to the developers of this software.  Apparently, they haven't done sufficient testing.

Here's a brief rundown of what is going on:

Regions of memory are referenced by object references in Java.  Object references in Java are nothing but pointers (according to the Java Language Specification)--thus, it is painfully clear that some part of your code is trying to refer to and use an object that cannot be referenced.  The reference that should point to your object does not hold a valid address (it's null).  This is why you get a NullPointerException (NPE in Java jargon).

Please report this issue to the developers of that software.  

Again, referring to my previous post, you can see why proprietary software don't cooperate with open software:

```

        at equis.metastock.MS4Java.repaint([DashoPro-V1.2-120198])

```

DashO is a proprietary obfuscation tool for Java designed to make it extremely difficult to reverse engineer the code and may make it incompatible with many other systems in the process.
The particular obfuscation in question obscures the source file and line number pointing at the source of the problem.  This makes debugging such problems even more difficult--exactly why
open software is easier to fix and update.

Regards,
Yesudeep.

---

### Post by yesudeep on 2007-05-27
For your Java plugin requirements, here's a listing from the multiverse Ubuntu repository:

```

**$ sudo aptitude search sun-java**
p   sun-java5-bin                                                          - Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture dependent files)       
p   sun-java5-demo                                                         - Sun Java(TM) Development Kit (JDK) 5.0 demos and examples                       
p   sun-java5-doc                                                          - Sun JDK(TM) Documention -- integration installer                                
p   sun-java5-fonts                                                        - Lucida TrueType fonts (from the Sun JRE)                                        
p   sun-java5-jdk                                                          - Sun Java(TM) Development Kit (JDK) 5.0                                          
p   sun-java5-jre                                                          - Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture independent files)     
p   sun-java5-plugin                                                       - The Java(TM) Plug-in, Java SE 5.0                                               
p   sun-java5-source                                                       - Sun Java(TM) Development Kit (JDK) 5.0 source files                             
**i   sun-java6-bin                                                          - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)**
p   sun-java6-demo                                                         - Sun Java(TM) Development Kit (JDK) 6 demos and examples                         
p   sun-java6-doc                                                          - Sun JDK(TM) Documention -- integration installer                                
p   sun-java6-fonts                                                        - Lucida TrueType fonts (from the Sun JRE)                                        
p   sun-java6-javadb                                                       - Java(TM) DB, Sun Microsystems' distribution of Apache Derby                     
p   sun-java6-jdk                                                          - Sun Java(TM) Development Kit (JDK) 6                                            
[B]i   sun-java6-jre                                                          - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)       
i   sun-java6-plugin                                                       - The Java(TM) Plug-in, Java SE 6        [/B]                                         
p   sun-java6-source                                                       - Sun Java(TM) Development Kit (JDK) 6 source files  

```

You can see what is installed on my computer to make Java applets work with Firefox (marked in **bold**).

Regards,
Yesudeep.

---

### Post by xavier_r on 2007-05-30
> **yesudeep said:**
> 
Here's a brief rundown of what is going on:

Regions of memory are referenced by object references in Java.  Object references in Java are nothing but pointers (according to the Java Language Specification)--thus, it is painfully clear that some part of your code is trying to refer to and use an object that cannot be referenced.  The reference that should point to your object does not hold a valid address (it's null).  This is why you get a NullPointerException (NPE in Java jargon).

Please report this issue to the developers of that software.  

;) Thanks
The software though is only maintained for Windows and not Linux...

I am now thinking if there's any way to retrieve those class files from the server
I know there's an obsfucator, but maybe, I think, I am missing the class that includes the function repaint...

Good, now i think this problem should shift to a JAVA forum :p

Still if anyone can run it from ubuntu... using appletviewer of any Java(Sun or Not) please reply... coz I want to stay in UBUNTU... booting to windows just to use this... argghh crap!!!

---

### Post by tors on 2007-05-30
```
export AWT_TOOLKIT=MToolkit && firefox http://charting.bseindia.com
```

---

### Post by xavier_r on 2007-05-30
> **tors said:**
> ```
export AWT_TOOLKIT=MToolkit && firefox http://charting.bseindia.com
```

F*CK!!! Are you a guru or something!!!
Thanks So MUCH So MUCH...

Dude, btw, can you explain what you did?
How did you figure that out?

---

