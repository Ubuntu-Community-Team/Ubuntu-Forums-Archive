---
title: "64 bit Java including plugin"
date: 2008-05-31
forum: General Help
---

### Post by stchman on 2008-05-31
Hello all.  I would like to know what packages I need to install for Ubuntu to get the following:

Java JDK
Java JRE
Java browser plugin

I want to use the open Java packages.

Would the openjdk-6-jdk package do it?

Would the gcjwebplugin-4.2 do it for Firefox?

Where does icedtea fit in?

Looks like if you install icedtea-java7-jdk, icedtea-java7-jre, and icedtea-java7-plugin you get it all.  Is this correct?

Thanks

---

### Post by dabang on 2008-05-31
Just go ahead and install openjdk:
```
sudo apt-get install openjdk-6-jdk icedtea-gcjwebplugin
```
This should leave you with a working JDK, JRE and Firefox java-plugin. I do not use it a lot, but never had problems.

If you have Sun's Java installed, too, you can choose the default with
```
sudo update-alternatives --config java
```
and
```
sudo update-alternatives --config javac
```

---

### Post by Sef on 2008-05-31
There is not currently a 64-bit plugin.  If you want some more info, click on the Java on 64-Bit Systems link.

---

### Post by dabang on 2008-05-31
> There is not currently a 64-bit plugin.
:confused::confused:

I'm running Firefox amd64 with icedtea-gcjwebplugin working fine...

---

### Post by stchman on 2008-05-31
> **Sef said:**
> There is not currently a 64-bit plugin.  If you want some more info, click on the Java on 64-Bit Systems link.

If you look in the repos icedtea-java7-plugin has a dependency called icedtea-gcjwebplugin and it has an amd64 version.  

There is no 64 bit Java plugin from SUN, I will agree to that.

[http://packages.ubuntu.com/hardy/icedtea-java7-plugin](http://packages.ubuntu.com/hardy/icedtea-java7-plugin)
[http://packages.ubuntu.com/hardy/icedtea-gcjwebplugin](http://packages.ubuntu.com/hardy/icedtea-gcjwebplugin)

---

### Post by stchman on 2008-05-31
> **dabang said:**
> Just go ahead and install openjdk:
```
sudo apt-get install openjdk-6-jdk icedtea-gcjwebplugin
```
This should leave you with a working JDK, JRE and Firefox java-plugin. I do not use it a lot, but never had problems.

If you have Sun's Java installed, too, you can choose the default with
```
sudo update-alternatives --config java
```
and
```
sudo update-alternatives --config javac
```

Yes, those packages are dependencies of the three icedtea packages.

---

### Post by TrashmanL on 2008-05-31
I installed all of the packages mentioned. I still have no Java. What folder is the icedtea plugin located? I was going to try making symbolic links in the plugins folder as my next step, but I couldn't find them...

---

### Post by stchman on 2008-06-01
> **TrashmanL said:**
> I installed all of the packages mentioned. I still have no Java. What folder is the icedtea plugin located? I was going to try making symbolic links in the plugins folder as my next step, but I couldn't find them...

It should just work.  If not go to a website that has Java and let Firefox install the plugin.  It should find it.  Worked on my 64 install.

---

### Post by TrashmanL on 2008-06-01
I Don't know, it's acting weird. Here's how it is right now: I have two versions of Firefox installed on here. Firefox 2, and Firefox 3 beta 5.
Believe it or not, that's how my laptop came! (I got it from linuxcertified.com) I also have Swiftfox, which apparently didn't see or is not compatible with Firefox 3 yet, so it installed on top of Firefox 2. 

After trying some things, it appears the plugins are installed, and just not working correctly.

If I open a java page in Firefox 3, it starts to work, but not long after I start using the applet, it freezes up.

If I used Firefox 2 or Swiftfox, I just get a plain white box. I don't even get the missing plugin... icon. If I go to pogo.com it tells me I need java installed, when I click on yes, it takes me to the Sun Java site. If I click on Verify, it says I have it installed, then redirects me back to pogo which says "Congratulations!" Then when I go to click on a game, it starts all over again...

My instincts right now say uninstall all the Java I have on here and try again. Maybe even uninstall Firefox 3.

---

### Post by kpagan on 2008-06-03
> 
Just go ahead and install openjdk:
```

sudo apt-get install openjdk-6-jdk icedtea-gcjwebplugin

```

This should leave you with a working JDK, JRE and Firefox java-plugin. I do not use it a lot, but never had problems.

If you have Sun's Java installed, too, you can choose the default with

```
sudo update-alternatives --config java
```

and

```
sudo update-alternatives --config javac
```



Well I have Ubuntu Hardy Heron 8.04 64bit and at random times my computer freezed. I suspected it was a Firefox 3.05b bug so I downgraded to firefox-2.
The problem was that there is no official 64bit java plugin.
The instructions above didn't do the trick.
So I followed the instructions found here : [http://plugindoc.mozdev.org/linux-amd64.html#java-blackdown]("http://plugindoc.mozdev.org/linux-amd64.html#java-blackdown")
The link that provide to download blackdown java does not work so here is a list of ftp mirrors to download blackdown java:

** North America**

   1. [ftp://ftp.tux.org/pub/java/](ftp://ftp.tux.org/pub/java/)
   2. [ftp://mirrors.ibiblio.org/pub/mirrors/blackdown/](ftp://mirrors.ibiblio.org/pub/mirrors/blackdown/) 

**Australia**

   1. [ftp://mirror.aarnet.edu.au/pub/java-linux/](ftp://mirror.aarnet.edu.au/pub/java-linux/) 

**Austria**

   1. [ftp://gd.tuwien.ac.at/opsys/linux/java/](ftp://gd.tuwien.ac.at/opsys/linux/java/) 

**Belgium**

   1. [ftp://ftp.easynet.be/blackdown/](ftp://ftp.easynet.be/blackdown/)
   2. [http://ftp2.skynet.be/pub/ftp.blackdown.org/](http://ftp2.skynet.be/pub/ftp.blackdown.org/)

**Denmark**

   1. [ftp://sunsite.dk/mirrors/java/java-linux/](ftp://sunsite.dk/mirrors/java/java-linux/) 

**Finland**

   1. [ftp://ftp.funet.fi/pub/Linux/java/jdk/](ftp://ftp.funet.fi/pub/Linux/java/jdk/) 

**France**

   1. [ftp://ftp.oleane.net/pub/java-linux/](ftp://ftp.oleane.net/pub/java-linux/) 

**Germany**

   1. [ftp://ftp.gwdg.de/pub/languages/java/linux/](ftp://ftp.gwdg.de/pub/languages/java/linux/)
   2. [ftp://ftp.informatik.hu-berlin.de/pub/Java/Linux/](ftp://ftp.informatik.hu-berlin.de/pub/Java/Linux/) 

**Hungary**

   1. [ftp://xenia.sote.hu/pub/mirrors/java.blackdown.org/](ftp://xenia.sote.hu/pub/mirrors/java.blackdown.org/) 

**Italy**

   1. [http://mirrors.publicshout.org/java-linux/](http://mirrors.publicshout.org/java-linux/)
       

**Netherlands**

   1. [ftp://ftp.nluug.nl/pub/languages/java/jdk](ftp://ftp.nluug.nl/pub/languages/java/jdk)

**Romania**

   1. [ftp://archive.logicnet.ro/mirrors/ftp.tux.org/](ftp://archive.logicnet.ro/mirrors/ftp.tux.org/) 

**Spain**

   1. [ftp://ftp.cica.es/pub/java-linux/](ftp://ftp.cica.es/pub/java-linux/) 

**Switzerland**

   1. [ftp://mirror.switch.ch/mirror/java-linux/](ftp://mirror.switch.ch/mirror/java-linux/)

**United Kingdom**

   1. [ftp://ftp.uk.linux.org/pub/linux/java/](ftp://ftp.uk.linux.org/pub/linux/java/)
   2. [ftp://ftp.mirrorservice.org/sites/ftp.blackdown.org/java-linux/](ftp://ftp.mirrorservice.org/sites/ftp.blackdown.org/java-linux/) 

After that do the following
```

Java Runtime Environment 1.4.2 (Blackdown)
Version: 1.4.2_03
SeaMonkey 1.1a, Firefox 2.0: Works Well
FAQ: Java FAQ

   1. Download Blackdown JRE
   2. Open a terminal, and change to the directory where you wish to install the JRE (eg. /usr/java)
   3. Run the Blackdown JRE package executable. This will extract the JRE in the current directory.
   4. Run the following command: ln -s ./j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so ~/.mozilla/plugins/libjavaplugin_oji.so

Important! It is critical that you create a symbolic link to the Java plugin rather than copying it. If you copy it, your browser will crash whenever you load a page that has a Java applet. 

```
*Taken from [http://plugindoc.mozdev.org/linux-amd64.html#java-blackdown]("http://plugindoc.mozdev.org/linux-amd64.html#java-blackdown")*

It is the only solution that worked in my case even it is not the best. 
I am able to play games at [www.pogo.com](www.pogo.com) but I cannot run the speedtest applet found here: [http://speedtest.forthnet.gr]("http://speedtest.forthnet.gr")
Also I didn't want to install firefox32 and install the 32bit plugins.
In my previous Ubuntu version (Gutsy) I had firefox32 with the plugins but it kept randomly crashing.

---

### Post by TrashmanL on 2008-06-03
:-( I've tried everything above, nothing works.
I uninstalled Firefox 3. I downloaded the amd64 version of blackdown, extracted it to /usr/lib/jvm/jre1.4.2 and created symbolic links in all the plugins directories. I've done likewise with 32bit Java 1.6, and with openjdk. I just don't know what to do anymore :-(.

---

### Post by alexou2648 on 2008-06-04
There is a major issue about the amd64-built (and maybe in 32 bits too?) icedtea-gcjwebplugin, it doesn't work with SSL (https). I checked almost everywhere about that point, and I haven't found anything yet to solve this problem. That really sucks. :mad:

---

### Post by TrashmanL on 2008-06-04
I definitely can't get openjdk working. It's like Mozilla/Firefox doesn't even see the plugin when I put the symbolic link in. (about:plugins doesn't show any java) The 32 bit version, almost works. It was the one that gave me a java screen before (that would freeze shortly after) on one of the versions. 

After I uninstalled everything and tried to reinstall, the 32 bit version does come up in Swiftfox only (not Seamonkey or Firefox) when I type about:plugins. However, it still will not run any java. When I try I get errors similar to this in the Java Console:

load: class testvmDynamicJavaCom.class not found.
java.lang.ClassNotFoundException: testvmDynamicJavaCom.class
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:194)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:640)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:786)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2108)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:715)
	at sun.applet.AppletPanel.run(AppletPanel.java:369)
	at java.lang.Thread.run(Thread.java:619)

---

### Post by TrashmanL on 2008-06-22
For some people, apparently this stuff worked. For those, like me, who still couldn't get things to work, you may want to try this post:

[http://ubuntuforums.org/showthread.php?t=202537]("http://ubuntuforums.org/showthread.php?t=202537")

---

### Post by TrashmanL on 2008-08-04
Hmm... I haven't tested it with everything yet, but after the latest update to Firefox 3, Java appears to be working using IcedTea for me, which it was not before. (funny thing is I didn't reinstall or update IcedTea)

I noticed when I upgraded it actually uninstalled the xulrunner plugin saying the version wasn't compatible. I don't know if that has anything to do with it or not.

Anyone else had any new luck with it?

I still have a 32-bit browser installed, as the 64 bit IcedTea java seems to be working slower than the 32-bit Sun Java at the moment, but at least it's starting to work for me.

---

### Post by tuxxy on 2008-08-04
I use the GCJ java, 32bit plugin runs ok for me on 64bit

---

