---
title: "Java SDK"
date: 2004-10-28
forum: General Help
---

### Post by jcscar on 2004-10-28
I am pretty much a newby to Linux..  I have found a program called gedit I have been using for java editing.  However I am use to using textpad for windows.
I have download the free-java-sdk's and it tells me to set JAVA_HOME environment vairable to /usr/lib/fjsdk and to add /usr/lib/fjsdk/bin at the beginning of your PATH.

Where do I add this in Ubuntu?

Is there a away I can hit a key sequence in gedit or some similar program to make it compile and run my java like in textpad?

Thanks in advance!

---

### Post by ubuntu-geek on 2004-10-28
Welcome to the forums.. this will probably work better for your needs then gedit.
 
 [http://jedit.org/](http://jedit.org/)

---

### Post by jdong on 2004-10-28
That is a _REALLY_ cool editor. Thanks.

---

### Post by jcscar on 2004-10-28
I don't understand how to install.

I come up with this error
```
root@mashed:/home/jcscar # java -jar jedit42install.jar
created the glasspane: javax.swing.JPanel[JPanel]
Created ContentPane: javax.swing.JPanel[JPanel]
update UI not overwritten in class: javax.swing.JRootPane[JComponent]
UIDefaults.getUIError: failed to locate UI class:EditorPaneUI
java.lang.NoSuchMethodError
   at installer.SwingInstall$TextPanel.SwingInstall$TextPanel (SwingInstall.java:344)
   at installer.SwingInstall.SwingInstall (SwingInstall.java:66)
   at installer.Install.main (Install.java:35)
   at java.lang.VirtualMachine.invokeMain (VirtualMachine.java)
   at java.lang.VirtualMachine.main (VirtualMachine.java:92)
```

---

### Post by jcscar on 2004-10-31
I got rid of the free java sdk available in the packages and installed from java.com   and it all works now. Thanks a bunch.

---

### Post by luiska on 2004-10-31
You can add it either in 
/etc/profile
then it will be available to all users or
~/.bash_profile
but then it is only in that users path

If somenone else wondered :)

---

### Post by rupert on 2004-11-18
Does jedit have a function like in eclipse to browse the possible commands by pressing ctrl + space.
hope you know what i mean.

greets

---

### Post by jdong on 2004-11-18
[QUOTE=jcscar]I got rid of the free java sdk available in the packages and installed from java.com   and it all works now. Thanks a bunch.[/QUOTE]
tsk tsk tsk, another person under the Soviet Public License... LOL

Can't blame you; I'm using Sun JDK 1.5.0, too!

---

### Post by viorel on 2004-11-19
I don't know if you ever heard about BlueJ, but it is a really simple (but very handy) Java IDE. I used a lot while learning Java. It is free and easy to install. You can get it here: [http://www.bluej.org/download/download.html](http://www.bluej.org/download/download.html)

Let me know if you have problems installing (should go pretty smooth, visual installer).

---

### Post by jwenting on 2004-11-19
[QUOTE=rupert]Does jedit have a function like in eclipse to browse the possible commands by pressing ctrl + space.
hope you know what i mean.

greets[/QUOTE]

not that I know of, but it's been a while since I used it and someone may have added it since.
I'm partial to vi  on systems where I can't run Eclipse or JBuilder.

---

### Post by rupert on 2004-11-19
when i have custom classes, where can i put them that they are global?
I have a script that come with classes, but it only explains it for windows.
If i can put my custom classfolders somewhere so that every editor can find and use them would be great.
DO they have an io and an auto folder by default?

PS:Maybe I got it, but now i get the following

```

Exception in thread "main" java.lang.NoClassDefFoundError: javakurs/io/AusgabeFenster
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at javakurs.io.Ausgabe.<clinit>(Ausgabe.java:31)
	at BeispielApp.main(BeispielApp.java:7)
Process java exited with code 1

```
thx

---

### Post by offby1 on 2004-12-26
[QUOTE=luiska]You can add it either in 
/etc/profile
then it will be available to all users or
~/.bash_profile
but then it is only in that users path

If somenone else wondered :)[/QUOTE]

I have done this to add JAVA_HOME, ANT_HOME, and CATALINA_HOME to my environment, but setting (and exporting) them in /etc/profile has not resulted in them appearing as part of my environment.  Apparently /etc/profile is not being read for some reason, can anyone offer any insight into this?

---

### Post by amerigo5 on 2004-12-27
You can follow the instructions here: [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

### Post by offby1 on 2004-12-27
[QUOTE=amerigo5]You can follow the instructions here: [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)[/QUOTE]

Actually, what I've learned is that /etc/environment is the best place to put those.  Carries over across boots, and is available in non-bash shells as well as in X11

---

