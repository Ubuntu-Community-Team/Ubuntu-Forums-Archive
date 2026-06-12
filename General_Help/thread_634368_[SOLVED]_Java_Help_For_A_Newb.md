---
title: "[SOLVED] Java Help For A Newb"
date: 2007-12-07
forum: General Help
---

### Post by silentabe939 on 2007-12-07
Okay so about four days ago i accidentelly formatted my HDD and instaled Ubuntu 7.10.  Over the past couple of days I have gotten most everything working.  Except Java on Opera.  Vis-a-vis I need help.  Whoever wants to help just tell me what I need to do and what you guys need to know.  Thanks.

---

### Post by jespdj on 2007-12-07
I don't use Opera, but here are instructions to get the newest version of Sun's Java installed and working.

First, install Sun Java 6:
```
sudo apt-get install sun-java6-plugin
```
Then, make sure that this is the default version of Java that the system uses:
```
sudo update-alternatives --config java
```
In the list that's displayed, select Sun Java 6.

Then restart your browser and see if it works.

---

### Post by silentabe939 on 2007-12-07
Okay so I tried that and sadly it still is not working.  What else could I try.

---

### Post by approaching on 2007-12-07
on their website, they mention that you have to enable java for opera if you are on linux. this should help you out.

[http://www.opera.com/support/search/view/459/](http://www.opera.com/support/search/view/459/)

but make sure that your jre is actually working before you go and beat your head against the wall.

---

### Post by silentabe939 on 2007-12-08
java works but flash seems to be horribly broken

---

### Post by taurus on 2007-12-08
> **silentabe939 said:**
> java works but flash seems to be horribly broken

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by Elegorod on 2007-12-08
In Opera, path to Java must be set.
Tools - Preferences - Advanced - Content
Check Enable Java, press Java options, and choose java path. My path is /usr/lib/jvm/java-6-sun/jre/lib/i386
To enable flash, download Flash installer (it's .tar.gz archive), decompress the archive and copy libflashplayer.so to /usr/lib/opera/plugins/

---

### Post by silentabe939 on 2008-02-12
i Consider this solved.  Thanks!

---

### Post by apetresc on 2008-02-12
> **silentabe939 said:**
> i Consider this solved.  Thanks!

Great :D You should go to "Thread Tools -> Mark Thread as Solved" in that case.

---

