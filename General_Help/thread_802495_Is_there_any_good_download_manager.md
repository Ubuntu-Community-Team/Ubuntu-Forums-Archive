---
title: "Is there any good download manager ?"
date: 2008-05-21
forum: General Help
---

### Post by Hessesian on 2008-05-21
When I switched to linux, the first thing I missed was good download manager, like IDM I used to have on my winXP, with segmentation downloads, resume, nice intuitive GUI, integrated with my browser (opera) and that is able to download from rapidshare, I spent hours searching and testing, with no succes. So my question stands: Is there any good download manager ? Or only crappy managers that have no gui and integration with my browser, I'm searching for something that can atleast download from rapidshare with atleast 2 segments.... is there any answer to my question ?

---

### Post by justin whitaker on 2008-05-21
> **Hessesian said:**
> When I switched to linux, the first thing I missed was good download manager, like IDM I used to have on my winXP, with segmentation downloads, resume, nice intuitive GUI, integrated with my browser (opera) and that is able to download from rapidshare, I spent hours searching and testing, with no succes. So my question stands: Is there any good download manager ? Or only crappy managers that have no gui and integration with my browser, I'm searching for something that can atleast download from rapidshare with atleast 2 segments.... is there any answer to my question ?

I use DownThemAll with Firefox.

---

### Post by NightwishFan on 2008-05-21
Downthemall extension. axel or wget on command line. gwget and kget for gui. (kget is great) Try them all.

---

### Post by Hessesian on 2008-05-21
> **NightwishFan said:**
> Downthemall extension. axel or wget on command line. gwget and kget for gui. (kget is great) Try them all.

Well, I tryed all managers you listed except donwthemall because I don't use Fx but Opera. None of those managers could download from rapidshare :-/ Are there any other options ?

---

### Post by Steveway on 2008-05-21
For Rapidshare and other one-click-hosters: jDownloader
It is not in the repositories but Google will tell you everything you need to know.

---

### Post by Hessesian on 2008-05-21
jDownloader did the job for now :) 

Thank you

---

### Post by NeQaSh on 2008-05-29
links 4 dl jdownloader  :guitar:

[http://jdownloader.ath.cx/download.php](http://jdownloader.ath.cx/download.php)

---

### Post by nycste on 2008-07-16
whats the best way to install jdownloader? anyone make a .deb package for it?

---

### Post by Steveway on 2008-07-16
> **nycste said:**
> whats the best way to install jdownloader? anyone make a .deb package for it?

Just download it, unpack it and start it by doubleclicking on jdownloader.jar (Providing that the Java-Runtime-Environment is installed.)

---

### Post by VMC on 2008-07-16
There's already this exact same topic opened here:
[http://ubuntuforums.org/showthread.php?t=851198](http://ubuntuforums.org/showthread.php?t=851198)

---

### Post by nycste on 2008-07-16
> **Steveway said:**
> Just download it, unpack it and start it by doubleclicking on jdownloader.jar (Providing that the Java-Runtime-Environment is installed.)

thanks for your quick reply but it hasnt helped

i did what u said and basically when i open jdownloader.jar the compression program opens up, i have java installed

thx, sryz ima newber

> **VMC said:**
> There's already this exact same topic opened here:
[http://ubuntuforums.org/showthread.php?t=851198](http://ubuntuforums.org/showthread.php?t=851198)

yea i know im reading both, ill copy and paste the info once i get it working in other thread

---

### Post by Steveway on 2008-07-16
> **nycste said:**
> thanks for your quick reply but it hasnt helped

i did what u said and basically when i open jdownloader.jar the compression program opens up, i have java installed

thx, sryz ima newber



yea i know im reading both, ill copy and paste the info once i get it working in other thread

Apperantly .jar sn't asociated to java. depending on your filemanager and desktop-environment:
Right-click on the file, select Open-with, select the java-runtime-environment and check alway open with. If java-runtime-environment is not in the list then choose costume-command and simply type java in it.
That should do the trick.
If it doesn't start the try finding the case of error by opening it through a terminal with:
java /path/to/jdownloader.jar
And see what it tells you.

---

### Post by nycste on 2008-07-16
> **Steveway said:**
> Apperantly .jar sn't asociated to java. depending on your filemanager and desktop-environment:
Right-click on the file, select Open-with, select the java-runtime-environment and check alway open with. If java-runtime-environment is not in the list then choose costume-command and simply type java in it.
That should do the trick.
If it doesn't start the try finding the case of error by opening it through a terminal with:
java /path/to/jdownloader.jar
And see what it tells you.

ok thanks well i guess ill be annoying as possible to learn as much as possible

i have 2 options in doing your advice 

1.OpenJDK Java Runtime
2.Sun java 6 Runtime

which do u advise just so i know, thanks

---

### Post by hariprs on 2008-07-16
Hi,
DownloadthemAll works well with rapidshare.

---

### Post by Steveway on 2008-07-17
> **nycste said:**
> ok thanks well i guess ill be annoying as possible to learn as much as possible

i have 2 options in doing your advice 

1.OpenJDK Java Runtime
2.Sun java 6 Runtime

which do u advise just so i know, thanks

Option 2 should be the correct one.

---

### Post by nycste on 2008-07-17
> **Steveway said:**
> Option 2 should be the correct one.

im about to giveup on this topic lol nothing will work

ok so i told it to open with option 2. nothing happened, tried option 1 nothing happened

then attempted to open from terminal

```
sudo java JDownloaderContainer.jar
Exception in thread "main" java.lang.NoClassDefFoundError: JDownloaderContainer/jar
Caused by: java.lang.ClassNotFoundException: JDownloaderContainer.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)

```

and i did that without sudo so just sharing the issues

---

### Post by nycste on 2008-07-17
just saw someone saying to open java things iwth this command so i tired

java -jar JDownloaderContainer.jar
Failed to load Main-Class manifest attribute from JDownloaderContainer.jar

---

### Post by Steveway on 2008-07-18
> **nycste said:**
> im about to giveup on this topic lol nothing will work

ok so i told it to open with option 2. nothing happened, tried option 1 nothing happened

then attempted to open from terminal

```
sudo java JDownloaderContainer.jar
Exception in thread "main" java.lang.NoClassDefFoundError: JDownloaderContainer/jar
Caused by: java.lang.ClassNotFoundException: JDownloaderContainer.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)

```

and i did that without sudo so just sharing the issues

Don't use sudo and you should open a file called JDownloader.jar and not JDownloaderContainer.jar. That could be the problem.

---

### Post by nycste on 2008-07-18
> **Steveway said:**
> Don't use sudo and you should open a file called JDownloader.jar and not JDownloaderContainer.jar. That could be the problem.

ok for some odd reason 

JDownloader.jar wasnt in my extracted files

so i went back to compressed file, opened it up and look what i found the file

just doubleclicked it and its installed, now to figure it out sometime thats stage 2 and wont involve this forum unless i need more help so thanks

---

