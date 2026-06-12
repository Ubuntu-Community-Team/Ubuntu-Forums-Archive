---
title: "Strange JAVA_HOME Problem"
date: 2008-06-05
forum: General Help
---

### Post by tberman333 on 2008-06-05
I just upgraded to 8.02 and I have having a strange problem with JAVA_HOME.

I run a TOMCAT server on my Ubuntu machine.  TOMCAT needs Java to run (and I think it needs JAVA_HOME defined).  When I boot my machine, TOMCAT starts as normal (so I think it can find JAVA_HOME).  The problem is, when I use the terminal to try to stop TOMCAT (sudo /usr/local/tomcat/bin/shutdown.sh), I get a message that says:

Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

I have tried to set JAVA_HOME in both the .bashrc file and in the /etc/environment file and I get the same error either way.

I have also tried both of these lines in my /etc/environment:

JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06/

JAVA_HOME=/usr/lib/jvm/java-6-sun/

and neither of these seem to work.

As a note, when I run ls /usr/lib/jvm  the following is returned:

java-6-sun  java-6-sun-1.6.0.06

If anyone has any ideas how to fix this it would be much appreciated.  I need to do an upgrade on one of my web-apps running on TOMCAT and I can't do the upgrade until I am able to stop the TOMCAT service.

THANKS!!

---

### Post by jamesstansell on 2008-06-05
Normally ~/.bashrc /etc/environment are only read when you login, so it would make sense to login again for changes to take effect.

In ~/.bashrc the variable needs to be exported, so you might try

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun/
```

Note that you can also run the export command directly and then you should be setup to run the shutdown.sh script.

---

### Post by tberman333 on 2008-06-05
Thanks for the suggustion.  I had the correct code in my ~/.bashrc file.  Also, I had loged off and back on after each change (even rebooted the machine to see if that worked...  still nothing.

I tried to just run the export command right in the terminal.  It did not return any message when I ran that command (export JAVA_HOME=/usr/lib/jvm/java-6-sun/), but I still got the JAVA_HOME not set error when I tried to run shutdown.sh

Any other ideas???

---

### Post by jamesstansell on 2008-06-06
> **tberman333 said:**
> Any other ideas???

That makes it sound like shutdown.sh is trying to read JAVA_HOME from somewhere beside the environment. I guess a configuration file may be possible?

I haven't played with Tomcat much in the last 5 years, and certainly not since January.  But if I can find some time this weekend I'll try to install it and take a look.

What version of tomcat do you have installed?  Did you get it from the ubuntu repository or from apache.org or from somewhere else?  I'm just hoping to be able to reproduce what you are seeing.

Regards,

-james.

---

### Post by tberman333 on 2008-06-07
Thank you very much for taking the time to look into this for me!  

I am running Tomcat 6.0.14

I installed it from the Appache website (using wget [http://apache.hoxt.com/tomcat/tomcat-6/v6.0.14/bin/apache-tomcat-6.0.14.tar.gz](http://apache.hoxt.com/tomcat/tomcat-6/v6.0.14/bin/apache-tomcat-6.0.14.tar.gz))

Also, just so you know, I was able to startup and shutdown tomcat on 7.10 (Gutsy Gibon).  I noticed the problem for the first time after upgrading to 8.02.

Thanks again and let me know if you need any other information from me, or want me to test anything out for you.

Todd

---

### Post by jamesstansell on 2008-06-08
> **tberman333 said:**
> I am running Tomcat 6.0.14

I installed it from the Appache website (using wget [http://apache.hoxt.com/tomcat/tomcat-6/v6.0.14/bin/apache-tomcat-6.0.14.tar.gz](http://apache.hoxt.com/tomcat/tomcat-6/v6.0.14/bin/apache-tomcat-6.0.14.tar.gz))

Also, just so you know, I was able to startup and shutdown tomcat on 7.10 (Gutsy Gibon).  I noticed the problem for the first time after upgrading to 8.02.


Hi Todd,

I just downloaded tomcat using the link you gave above.  I'm not sure if I'll have time to install it today.

Sometime recently Ubuntu changed /bin/sh from being bash to being dash.  That may be the root of the issue.  A quick way to try with bash is with this command:
```
/bin/bash ./shutdown.sh
```

Honestly, though, I couldn't guess right now how that would make the difference you're seeing.

Regards,

-james.

---

### Post by tberman333 on 2008-06-08
I tried that command and it did not work.  I assume the full command I should use would be:

```
sudo /bin/bash /usr/local/tomcat/bin/shutdown.sh
```

If this is incorrect, please let me know I will will try something different (by the way, the exact code you had in your last post gave me a message of file or directly not found).

I appreciate the help in trying to get this resolved!

Todd

---

### Post by jamesstansell on 2008-06-09
> **tberman333 said:**
> I tried that command and it did not work.  I assume the full command I should use would be:

```
sudo /bin/bash /usr/local/tomcat/bin/shutdown.sh
```

If this is incorrect, please let me know I will will try something different (by the way, the exact code you had in your last post gave me a message of file or directly not found).

I appreciate the help in trying to get this resolved!

Todd

I wouldn't normally think you would need to use the sudo for shutdown.sh - but I'm not positive.

You are right though that the idea is to reference the shutdown.sh script.  So you can either do a full path (/usr/local/.../) or you can cd to the directory and use a relative path (./)  Some scripts run better if your current directory is where they are, but I don't know exactly about shutdown.sh yet.

---

### Post by tberman333 on 2008-06-09
That worked.  When I changed to the directly and used

```
/bin/bash ./shutdown.sh
```

It worked.

Now there is a problem starting it back up, but I think this may be an easier one to solve (as it seems to just be permissions...

If I use 

```
/bin/bash ./startup.sh
```

I get this error message:
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun-1.6.0.06/
touch: cannot touch `/usr/local/tomcat/logs/catalina.out': Permission denied
/usr/local/tomcat/bin/catalina.sh: 338: cannot create /usr/local/tomcat/logs/catalina.out: Permission denied

Then if I use

```
sudo /bin/bash ./startup.sh
```

I get this again

Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program


It is almost like my root user does not see that JAVA_HOME or JAVA_JRE is set?

---

### Post by tberman333 on 2008-06-09
I have been playing with this a little more.  I logged off and back on my machine (which restarted Tomcat and also got rid of any environments i set in terminal during).

I then did a CD to the tomcat/bin directory and ran ./shutdown.sh (without the /bin/bash).  When doing this, the tomcat server did stop successfully, but returned an error message:

```
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun-1.6.0.06/
Jun 9, 2008 7:19:44 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop: 
java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
	at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
	at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
	at java.net.Socket.connect(Socket.java:519)
	at java.net.Socket.connect(Socket.java:469)
	at java.net.Socket.<init>(Socket.java:366)
	at java.net.Socket.<init>(Socket.java:180)
	at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:337)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:415)

```

After it is shutdown, I still can't restart as I get the same error message as in my previous post.

At this point, since I can shut it down, I am able to make the changes I needed to (to the web ap I am running), and then I just log off and back on the machine to restart it, but it still seems like some kind of bug that it can't be restarted from terminal (when it could in 7.10)

---

### Post by jamesstansell on 2008-06-09
> **tberman333 said:**
> 
After it is shutdown, I still can't restart as I get the same error message as in my previous post.

At this point, since I can shut it down, I am able to make the changes I needed to (to the web ap I am running), and then I just log off and back on the machine to restart it, but it still seems like some kind of bug that it can't be restarted from terminal (when it could in 7.10)

Perplexing and interesting at the same time.

To start with, since you installed by downloading from apache instead of the ubuntu repository then I'm inclined to think that any differences between 7.10 and 8.04 are symptoms, rather than a primary issue.

I installed tomcat on my 8.04 machine this afternoon and played with the scripts (but didn't actually run tomcat yet.)  startup.sh and shutdown.sh both call catalina.sh.  Also, if you add a script called setenv.sh in the same directory then you can define whatever variables you want to - the main one to consider is probably JAVA_HOME.  That lets you set it so the tomcat scripts can read the value, but the rest of the system doesn't have to be bloated with the JAVA_HOME setting for tomcat.

I'm confused why tomcat only starts for you when you log off and back on.  You're running startup.sh in both cases, right?

At any rate, I think adding the following line to a new file named setenv.sh in your /usr/local/tomcat/bin/ directory will go a long way for you.
```
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06/
```

---

### Post by tberman333 on 2008-06-09
That did it!  Thank you very much for your help!

---

### Post by maiatoday on 2008-06-10
Thank you this also solved my problem when trying to get openlaszlo to work. I am adding this post for search purposes.

---

### Post by dgib on 2008-06-23
bump =D

just want to say, this solution fixed my issue also... the same issue as everybody else had.

My issue came about the other day after upgrading to Hardy... This is the second time i've upgraded distro's and had java die on me :s possible problem?

anyway, Im just happy it works, so thank you to jamesstansell for the nice solution :)

---

