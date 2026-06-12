---
title: "Openoffice crashes on exit and some Java issues"
date: 2008-06-18
forum: General Help
---

### Post by vincentaii on 2008-06-18
Hi guys,

I'm an off-and-on ubuntu user, but of late I'm more on than off. However, I have a couple of problems i just can't seem to figure out. My system's Kubuntu Hardy 64bit btw:

1. OpenOffice.org crashes on exit
Previously I did not have this problem, until it was upgraded to OOo 2.4.1 this morning. Now it crashes on every exit. At first i thought it had to do with the fact that Java isn't being detected by OOo (see 2nd problem), so i installed Openoffice.org-java-common as suggested in another thread, but the problem still persists. When it crashes, I get this in term:

KCrash: Application 'soffice.bin' crashing...
XIO:  fatal IO error 9 (Bad file descriptor) on X server ":0.0"
      after 124 requests (124 known processed) with 0 events remaining

2. Java isn't detected
I have Java installed (OpenJDK Runtime Environment (build 1.6.0-b09)), but it seems like no browser (i.e. Konqueror/Opera/Firefox) or any other proggie can detect it, even if I manually point it to the correct directory. I removed OpenJDK, installed Sun's but due to other issues that caused (seems no browser plugin yet for 64 bit), I'm trying OpenJDK again.

I've tried different suggestion in the other threads for the above with no success. Any help would be greatly appreciated. God bless!

Vincent

---

### Post by RapMasterC on 2008-06-18
I am having the same problem. I removed openoffice and reinstalled, it exited fine however as soon as I install the kde package (not sure of the name to call it) to it, openoffice would crash on exit.

---

### Post by vincentaii on 2008-06-22
Hi Guys,

Some updates. I'm pretty sure (though not 100%) that the problem with OOo crashing on exit has nothing to do with my Java as I've managed to get it to detect the Java fine (though it is the only proggie that seems to be able to do so). I'm still at a loss as to what in fact is causing it though.

On the Java, with the recent announcement that OpenJDK has managed to replace all proprietary code with open ones, does this mean we'll soon see browser plugins for AMD64? Here's to hoping....

Vince

---

### Post by lanzailan on 2008-06-22
i'm also having problem with java... :confused:

---

### Post by old_salt on 2008-06-22
I noticed it after the Office update a few days ago as well. I've attached my crash bug report. Can't report this to KDE since this is a non-KDE app.

---

### Post by vincentaii on 2008-06-24
We're not alone.... [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/237660]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/237660")

Hope it gets sorted out.... it's not a show stopper, but it sure is annoying....

---

### Post by Zorael on 2008-06-24
As for your OpenJDK Java plugin issues, please post the output of the following command. Depending on the output, one command alone should fix things. *Provided* you've made sure not to actually *disable* Java in your browsers, of course.
```
$ ls -l `locate *plugins/*java*` /etc/alternatives/*java*plugin*
```

---

### Post by vincentaii on 2008-06-26
Hi Zorael,

I've run the command you mentioned and got this:

++Quote++

lrwxrwxrwx 1 root root 57 2008-06-26 20:43 /etc/alternatives/xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so

++Unquote++

I have absolutely no idea what it means though.

Java is enabled in Firefox, Opera and Konqueror. I also have the latest openjdk-6-jre,openjdk-6-jre-headless, openjdk-6-jre-lib, tzdata-java and icedtea-gcjwebplugin installed from the repos.

Hope you can make sense of this. Cheers!

---

### Post by Zorael on 2008-06-26
> **vincentaii said:**
> Hi Zorael,

I've run the command you mentioned and got this:

++Quote++

lrwxrwxrwx 1 root root 57 2008-06-26 20:43 /etc/alternatives/xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so

++Unquote++

I have absolutely no idea what it means though.

Java is enabled in Firefox, Opera and Konqueror. I also have the latest openjdk-6-jre,openjdk-6-jre-headless, openjdk-6-jre-lib, tzdata-java and icedtea-gcjwebplugin installed from the repos.

Hope you can make sense of this. Cheers!
I forgot some commands; please post the output of the following, as well.
```
$ locate *plugins/*java* | grep /usr/lib
$ dpkg -l *icedtea*
```

---

### Post by vincentaii on 2008-06-26
Ok, the first command (locate *plugins/*java* | grep /usr/lib) yielded no output whatsoever, while the second (dpkg -l *icedtea*) gave the following:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  icedtea-gcjweb 1.0-0ubuntu5   Java plugin based on IcedTea and gcjwebplugi
un  icedtea-java7- <none>         (no description available)

Cheers!

---

### Post by Zorael on 2008-06-26
Okay!

```
$ sudo aptitude install icedtea-java7-plugin        # not sure it's needed but, eh, might as well
$ sudo ln -s /etc/alternatives/xulrunner-1.9-javaplugin.so /usr/lib/mozilla/plugins/javaplugin.so
```
Restart browser.

---

### Post by vincentaii on 2008-06-27
Hi Zorael,

Followed as advised but still no luck.... I'm starting to think I should install the 32 bit edition of Ubuntu instead.... wonder would I suffer any performance loss though?

Thanks nonetheless Zorael, appreciate the help!

---

### Post by Zorael on 2008-06-27
On the topic of OO.o crashing, I submitted the apport report and confirmed the bug. Chris Cheney commented there saying he might have a solution. Hopefully he'll bring us up to speed soonish.

**vincentaii**: Your Java plugin *should* logically work by now. :< Let's make sure we have everything in place. Make your terminal window wide so as not to get truncating, especially for the first command. Also, please put the output inbetween ```
 tags.
[code]$ dpkg -l *java* | grep plugin
$ apt-cache policy icedtea-java7-plugin
$ ls -l `ls -w1 /usr/lib/mozilla/plugins/*java*` /etc/alternatives/xulrunner-1.9-javaplugin.so /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
```
It's hard to troubleshoot when not actually at the machine in question, heh.

---

### Post by vincentaii on 2008-06-27
Hi Zorael,

I saw Chris' reply on possibly having a solution, with it likely being an openoffice.org-gtk issue. Pardon my ignorance, but would the same apply to Kubuntu users as well? (Edit: My bad. Seems the openoffice.org-gtk problem is a "related" issue).

Okay, on the Java, this is what i got:

```
vincent@ubuntu:~$ dpkg -l *java* | grep plugin
un  ia32-sun-java6-plugin                      <none>                                             (no description available)
ii  icedtea-java7-plugin                       7~b24-1.6-0ubuntu5                                 Java plugin based on IcedTea and gcjwebplugi
un  sun-java6-plugin                           <none>                                             (no description available)

vincent@ubuntu:~$ apt-cache policy icedtea-java7-plugin
icedtea-java7-plugin:
  Installed: 7~b24-1.6-0ubuntu5
  Candidate: 7~b24-1.6-0ubuntu5
  Version table:
 *** 7~b24-1.6-0ubuntu5 0
        500 http://us.archive.ubuntu.com hardy/universe Packages
        100 /var/lib/dpkg/status

vincent@ubuntu:~$ ls -l `ls -w1 /usr/lib/mozilla/plugins/*java*` /etc/alternatives/xulrunner-1.9-javaplugin.so /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root    57 2008-06-26 20:43 /etc/alternatives/xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
-rw-r--r-- 1 root root 28088 2008-03-28 23:55 /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root    45 2008-06-27 19:39 /usr/lib/mozilla/plugins/javaplugin.so -> /etc/alternatives/xulrunner-1.9-javaplugin.so
```

And thanks for sticking with this, I greatly appreciate it.

---

### Post by Zorael on 2008-06-27
Are you using Firefox 2 or 3?  Anyway, open up a terminal and run firefox from there.
[list=1][*]Is Java mentioned in about:plugins? (Enter it in the address field.)
[*]If 1, is anything of interest output to the terminal when you navigate to a page with an applet? Example: [http://javatester.org/version.html](http://javatester.org/version.html).[/list]

---

### Post by Zorael on 2008-06-27
While helping to debug this I realize that mine isn't working either. If you're using Firefox 2, and it shows up in about:plugins yet still doesn't work, and it outputs "invalid browser function table" to the terminal, then we're in the same boat. It *does* work for me in Firefox 3, though I want to keep to Firefox 2 if at all possible.

I posted a new post at [http://ubuntuforums.org/showthread.php?t=842739](http://ubuntuforums.org/showthread.php?t=842739) to see if it's a common issue.

---

### Post by vincentaii on 2008-06-27
I'm using Firefox 2. Firefox 3 has problems with flash, which I need more than Java, so I guess I'm one of the few who've held off migrating just yet.

It's weird, when I open up "about: plugins", Java isn't mentioned anywhere. However, under "about: config", this is what I have pertaining to Java:

```
java.default_java_location_others   default   string   /usr/java
java.default_java_location_solaris   default   string   /usr/j2se
java.global_java_version_file   default   string   /etc/.java/versions
java.java_plugin_library_name   default   string   javaplugin_oji
java.private_java_version_file   default   string   ~/.java/versions
```

I tested the following which opened up the page but without starting the applet and without any output in the terminal (I just have that green jigsaw puzzle piece saying I don't have the plugin installed):

```
vincent@ubuntu:~$ firefox-2 http://www.javatester.org/version.html
```

I should maybe add that I can open up the OpenJDK Java Web Start just fine, though what good that does I'm not sure. Cheers.

---

### Post by vincentaii on 2008-06-28
Well, I finally (kinda) sorted it out. I removed Firefox, OpenJDK, IcedTea and the Kubuntu Restricted Extras packages via apt-get, and deleted the .mozilla folder, and started from scratch by installing Firefox 3, and reinstalling the Kubuntu Restricted Extras. Surprisingly I now have Java and Flash working, albeit a little buggy, in both Firefox and Konqueror but not Opera (heck, 2 out of 3 ain't bad).

I think when Ibex is a little more stable I'm going to install the i386 version. I don't think AMD64 support is quite there yet (though things may drastically change by the time Ibex goes final, who knows). Cheers!

---

