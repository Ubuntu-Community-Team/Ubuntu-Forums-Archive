---
title: "Install specific java online banking program"
date: 2005-06-12
forum: General Help
---

### Post by Kangaroo on 2005-06-12
Been using Ubuntu for quite some time now, and for me it's the best distro i've come across yet. However, i try to setup my bank online banking program, but it somehow just won't work. This seems to be a java program and it comes in an installer called "setup.bin".

[Here it is, if you wanna get your hands dirty ](http://www.zkb.ch/onba/download/setup.bin) 

After doing ```
chmod u+x setup.bin
``` and afterwards ```
./setup.bin
``` a graphical installer should appear, but all i get, is the following: 
lonestar@ubuntu:~$ ./setup.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:140)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:62)
        at java.awt.Window.init(Window.java:224)
        at java.awt.Window.<init>(Window.java:268)
        at java.awt.Frame.<init>(Frame.java:398)
        at java.awt.Frame.<init>(Frame.java:363)
        at com.zerog.ia.installer.Main.c(Unknown Source)
        at com.zerog.ia.installer.Main.main(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:324)
        at com.zerog.lax.LAX.launch(Unknown Source)
        at com.zerog.lax.LAX.main(Unknown Source)
GUI-

Being a noob, i couldn't figure out, what to do next. Can anyone pls point me in the right direction ?

B.T.W. After typing ```
java -version
``` i get this: 
java version "1.5.0_03"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_03-b07)
Java HotSpot(TM) Client VM (build 1.5.0_03-b07, mixed mode, sharing)

---

### Post by diebels on 2005-06-12
This file installs its own JavaRuntimeEnviroment, so maybe it's buggy and only works with that.

Remove your current JRE, and run the file with sudo, so it gets  the write permissions it needs when installing it's own JRE.

---

### Post by Kangaroo on 2005-06-13
Thanks for your tip. I have the sun j2re from the backports. 
Removed that with synaptic. Then, i tried: ```
sudo ./setup.bin
```

But i'm still getting the same result. I tried download the "setup.bin" again, to outrule any downloading problem.

---

### Post by diebels on 2005-06-13
Don't know. Mabye it only works with ms-java or something. I would have asked my bank if they have tested it in Linux, mac, freebsd, or only windows.

---

### Post by Kangaroo on 2005-06-14
It works on Linux. I have checked that with a test install of Suse 9.3, where it installed flawless. But since Ubuntu is my main desktop OS, i would like to get it 
to work with Ubuntu (somehow)

---

### Post by diebels on 2005-06-15
Hmm. Did suse 9.3 have a JRE installed? If so, what version?

You could try to install sun java [1.4.2 ](http://java.sun.com/j2se/1.4.2/download.html)in ubuntu.

Could be that the banking program is using some old java stuff that's removed or just not working in 1.5.

[QUOTE=http://www.zkb.ch/bin/entry/frame/onba/voraussetzung/index.html]Betriebssystem  	

Jedes Betriebssystem, für das es einen Internet Browser gemäss nachfolgender Spezifikation gibt.
	Windows 98/ME
Windows NT/2000/XP
Mac ab OS X (10.2.3)
JRE 1.4.1
Linux[/QUOTE]

---

### Post by Kangaroo on 2005-06-16
I have erased the harddisk with the suse 9.3 install, so can't check any more. But when i'll get round to do it, i'll probably re-install to have a glance at the java version there. 

Meanwhile i removed java 1.5 and downloaded j2re-1_4_2_08-linux-i586.bin
Then i made a .deb with 

```
fakeroot make-jpkg j2re-1_4_2_08-linux-i586.bin
``` 

and installed it with 

```
dpkg -i sun-j2re1.4*
``` 

But still getting the same result here. 

Well, 'til i get round to re-install suse 9.3 and check out what they do different, i'll be stuck here with the HTML-Version of the online bank (which is a bit less comfy) 

But we have better weather coming up this weekend (30°c) so that'll have to wait. 

Thanks anyway for your patience.

---

### Post by Kangaroo on 2005-06-18
I meanwhile had a chance to look at my SUSE installation (i thought i had erased it, but i had just put the HD in another computer of mine, not yet erased) 

The java version in Suse 9.3 is 1.4.2_06, so i guess i would have to hunt down a .deb with that java version for Ubuntu ?

---

### Post by pinkcactus on 2006-09-11
I've also had this problem using the ZKB online banking program. Due to missing support from ZKB's side (very disappointing!), I had to figure out another way to install it, wasting many hours but coming up with an easy solution.

The problem which is causing the error is that the installation program wants to use its own runtime environment (jre) and that one seems to be pretty buggy. So the solution is to run it using another jre. First make sure you have some version of the jre installed or download one at java.sun.com . Then run the folling command:

```
java -jar setup.bin
```
instead of
```
./setup.bin
```

Have fun and enjoy that beautiful java program ](*,) 

Simon

---

### Post by Lovejoy on 2006-09-11
I had the same problem with Java. I don't like all of the terminal inputting that I don't really understand anyway. So after looking at several different threads and checking out what 'Synaptic' showed installed on my system I tried a very simple fix, and it worked. By the way, I'm using Ubuntu Dapper Drake 6.06. Also I'm using all of the repositories that 'EasyUbuntu' accessed.

In Synaptic selecting the 'all' category on the left side, roll down and click to install 'java-common' then jump down and install 'sun-j2re1.5', 'sun-java5-bin', 'sun-java5-fonts', 'sun-java5-jre', and 'sun-java5-plugin'. Then of course click 'apply' at the top. After you accept the license questions it finishes the install.

Go to your website and everything should be there. It was for me. I had 'java-common' installed that thought I was in business, but it didn't work until I installed the 'sun- . . .' stuff.

Lovejoy

---

### Post by eha1990 on 2006-09-11
Does anyone know how to install Java Advanced Imaging?

I've followed the directions located at [http://java.sun.com/products/java-me...ALL-1_1_2.html](http://java.sun.com/products/java-me...ALL-1_1_2.html)

I downloaded the Java Advanced Imaging files at
[http://java.sun.com/products/java-me...oad-1_1_2.html](http://java.sun.com/products/java-me...oad-1_1_2.html)

---

