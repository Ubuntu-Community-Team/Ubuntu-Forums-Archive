---
title: "LibreOffice crashes - even on new user profile"
date: 2014-03-13
forum: General Help
---

### Post by ancaleth on 2014-03-13
So, of course it is only a few days until I have to hand in some  important stuff that I am currently writing on Libreoffice - and it  decides to go buggy on me.


I thought it was fixed - there  had been a series of power cuts, probably corrupting the user profile:  so I created a new one, and it seemed to solve the issue &#8211; for approx. 2  days I didn't have any crashes. However, Libreoffice just crashed on me  again. No power cuts in sight; though there was one hard reboot bc  ubuntu would not start up properly.


I was (!) running  Zotero in Libreoffice, but am not anymore on the new profile, because I  suspected it might if not cause, at least be aggrevating the problem. No  pattern I can speak of in the crashes. If I am not running  Firefox, they tend to happen less often, but they still happen. I  disabled the Java Runtime Environment in Libreoffice, and also then it  still happens. (And also that isn't really a longterm option, because I  would like to use Zotero again!)

Any help is much needed and appreciated. I am running ubuntu 13.10 on 64-bit Dell.


UPDATE: It seems LibreOffice might not appreciate too many copy-pastes coming from Firefox, sometimes including links -> crashes quite often when pasting links, but also when deleting them.

---

### Post by phidia on 2014-03-13
There are several threads on random crashing in Libre Office but [this one]("http://askubuntu.com/questions/41329/how-can-i-stop-libreoffice-from-randomly-crashing") looks most related-I think. After a crash OS or app there would be logfiles you can look through too.

Added later: Admittedly looking through logfiles can be tedious. Perhaps the best method is to open libre from cli/terminal, leaving that open and when/if there is a crash the terminal should contain some relevant info.

---

### Post by ancaleth on 2014-03-31
Thanks for the pointer. After finding some logfiles relating to Java:

> # A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f281dcc0398, pid=5353, tid=139810295699968
#
# JRE version: OpenJDK Runtime Environment (7.0_51) (build 1.7.0_51-b00)
# Java VM: OpenJDK 64-Bit Server VM (24.45-b08 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [libmergedlo.so+0x24a0398]  Window::GetWindow(unsigned short) const+0x1b8
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# If you would like to submit a bug report, please include
# instructions on how to reproduce the bug and visit:
#   [http://icedtea.classpath.org/bugzilla](http://icedtea.classpath.org/bugzilla)


I got rid of all Java versions I had by purging:
```
sudo apt-get purge icedtea-* openjdk-*
```  

Then checked to make sure they were gone:
```
sudo dpkg --list | grep -i jdk
```

I installed openJDK 7 and icedtea plugin: 
```
sudo apt-get install openjdk-7-jdk openjdk-7-jre
```


```
sudo apt-get install icedtea-plugin
```

No crashes so far. 

I have now upgraded to Libreoffice 4.2 and also re-integrated Zotero. Fingers crossed.

---

### Post by speartip on 2014-03-31
I've not been able to get on with LibreOffice since version 3.5.7. Crashes, freezes & the like.
So I completely purged LO, & installed OpenOffice from here:
[http://www.openoffice.org/download/](http://www.openoffice.org/download/)
Have nor had one issue since.
You might want to consider, if the crashes come back.

---

