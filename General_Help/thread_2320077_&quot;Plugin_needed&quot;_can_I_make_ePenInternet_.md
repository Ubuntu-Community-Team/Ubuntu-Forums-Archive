---
title: "&quot;Plugin needed&quot; can I make ePen/Internet Explorer work?"
date: 2016-04-10
forum: General Help
---

### Post by ZannaStar on 2016-04-10
I need to use Pearson's ePen to mark exams online. I've done this for three years previously using Windows XP, and every year I've been briefly confused about why ePen doesn't work, before I remember that it only works in Internet Explorer. This is the only reason I have ever wanted to use and the only occasion I ever use IE! Now I'm using Ubuntu 16.04, and thinking about how I am going to be able to fulfill my contracts this year. I have searched a little bit, but I have not found anything that seems up to date. The ePen minimum system requirements page as of April 2015 states that Windows Vista, 7, 8 or 8.1 are needed (though it worked fine last May/June in XP) and that IE 9 10 or 11 are needed. I suspect the OS is not important and that it would be possible to make it work in Firefox somehow, or if not, to use IE somehow. ePen uses a Java applet - when I try to open it in Firefox I see 'A plugin is needed to display this content'. Security is important, because the content handled on this page is secret, but users have to log in before entering the applet. I feel like I should be able to make it work with all its security features, but, I know nothing. Last year I spoke to the helpdesk about making ePen more compatible, and the response was amusement and 'that would be nice'. If anyone can share related experience or point me in a useful direction to learn how I can work around this problem, I will be very grateful!

---

### Post by coldraven on 2016-04-10
You will probably have to install Windows as a virtual machine. You can get the latest version of VirtualBox here: [https://www.virtualbox.org/](https://www.virtualbox.org/)
If you have a XP install disc you could use that but if you really need IE9 read the last section of this link. It seems that Microsoft have some ready made VMs that can be freely downloaded but I have never used them so I'm unable to say if they work.

[http://www.rdeeson.com/weblog/126/how-to-run-internet-explorer-7-8-and-9-in-linux-with-or-without-wine.html](http://www.rdeeson.com/weblog/126/how-to-run-internet-explorer-7-8-and-9-in-linux-with-or-without-wine.html)

---

### Post by yancek on 2016-04-10
You could try using "User Agent Switcher" or a similar Add-on to identify Firefox as IE.  On firefox, you should be able to do this from Tools, Add-ons and in the Search box in the upper right, type in User Agent Switcher and hit the Enter key.  The User Agent Switcher should show below and click install and try that.  If it doesn't work, it is simple enough to remove it.

---

### Post by coldraven on 2016-04-10
> **yancek said:**
> You could try using "User Agent Switcher" or a similar Add-on to identify Firefox as IE.  On firefox, you should be able to do this from Tools, Add-ons and in the Search box in the upper right, type in User Agent Switcher and hit the Enter key.  The User Agent Switcher should show below and click install and try that.  If it doesn't work, it is simple enough to remove it.
  That a good suggestion, try that first because it's a whole lot easier than my solution.

---

### Post by ZannaStar on 2016-04-10
Thanks a lot! I did want to avoid doing the VirtualBox thing, just because my HD is so tiny (32GB). That's my last resort.  I installed the User Agent Switcher add-on which seems really neat - selecting IE causes nearly everything to work really badly so it's obviously working ; ) Doing a bit more digging on the ePen site suggested that installing Oracle Java would help, so I used this page to do that [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html) And, progress! Now the plugin tries a lot harder to work! But eventually it times out. It looks like I'm having a 'security' issue. I enabled Java in firefox's security popup but the 'browser health check' says 'application blocked by Java security'. I can apparently make this work by setting a site exception in the Java Control Panel, but I can't find any evidence that this exists other than in Windows and OSX. My next step will be to research how I can manipulate Java's stupid security settings. Any help with that would be amazing, but hopefully I will be able to figure it out

---

### Post by coldraven on 2016-04-11
> Any help with that would be amazing, but hopefully I will be able to figure it out
Sorry, no Java here :(

---

### Post by ZannaStar on 2016-04-16
Actually, fixing the security settings was basic - searching in the dash located the control panel perfectly *blush* and entering site exceptions worked somewhat - the applet now tries to load. By reading its errors (about not being able to find requisite libraries) I have got closer to a solution, but still working on it. Optimistic!

---

### Post by ZannaStar on 2016-04-27
YESSSS solved it!! It was actually quite tricky for a n00b like me. This may not be the minimum steps needed but here is what I did.

**NOTE: no need to use a virtual machine or User Agent Switcher**

_How to make ePEN's Java Applet work in Firefox on 64-bit Ubuntu_
Step 1: Install Oracle Java 8 [from ppa]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")
Step 2: Go to the ePen site and Try to load the applet, answering 'run' 'allow' etc to any security warnings* You will probably need to click 'Activate Java' under the plugin icon
Step 3: The plugin will probably fail. Click for details and open the java console to see the error message. You will probably see something like 'Unsatisfied Link Error' cannot load 32-bit SWT libraries on 64-bit JVM To fix this, install the libraries and copy the swt-gtk-3.8.2.jar file to the place where java looks for libraries. If you see a different error, see Extra Step below.
```
# apt-get install libswt-gtk-3-jni libswt-gtk-3-java
# cp /usr/lib/java/swt* /usr/lib/jvm/java-8-oracle/jre/lib/ext
```
May be needed for some users:
Extra Step: If loading the applet fails with a message along the lines of: 'unable to load libraries' with a path along the lines of  /home/<username>/.swt/lib/linux/x86_64 fix it by making this symlink:
```
# ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64
```

*you can get rid of these security warnings permanently by telling Firefox to always allow java to run on this page and by setting a site exception in the Java Control Panel security options (search for Java in the dash)

Some explanation:
I read on [this answer]("http://stackoverflow.com/questions/17057686/swt-on-32-bit-and-64-bit-jre?lq=1") that java looks for libraries in <jvm>/jre/lib/ext and in [this question]("http://stackoverflow.com/questions/2921193/swt-on-windows-64-bit") what SWT libraries look like - the requisite file is called 'swt.jar'. Hunting through java's many directories I found
```
zanna@zanna-X205TA:~$ cd /usr/share/java
zanna@zanna-X205TA:/usr/share/java$ ls -ltra
total 520
lrwxrwxrwx   1 root root     32 Jul  2  2013 swt.jar -> ../../lib/java/swt-gtk-3.8.2.jar
lrwxrwxrwx   1 root root     32 Jul  2  2013 swt-gtk-3.8.jar -> ../../lib/java/swt-gtk-3.8.2.jar
```
seeing that swt.jar is a symlink to a file I installed at step 4 (reading [this documentation]("http://packages.ubuntu.com/xenial/amd64/libswt-gtk-3-java/filelist") helped me figure this out) I was able to guess that that was the file I needed to drop into <jvm>/jre/lib/ext

Edit: Out of curiosity (and to use FOSS wherever possible) I tried uninstalling Oracle Java, installing OpenJDK 8 and Iced Tea plugin. I could not make the applet work this way

---

### Post by tom-literaryconnections on 2016-06-09
> **rose-anna-bleasdale said:**
> YESSSS solved it!! It was actually quite tricky for a n00b like me. 

**Just to say - many, many thanks! **I'd been struggling using ePen with IE on a laptop and hating it. Following your instructions (including Step 3 but not extra step) and within a few minutes ePen now works in Firefox on my desktop and big screen. It installed JRE version 1.8.0_91, which is more recent than the one recommended, but no problems so far, and it's not only much faster and clearer but also no longer forces me to dismiss not one but two update messages *every* *time* a new batch of scans is uploaded! 

*[Linux Mint 17.3]*

---

