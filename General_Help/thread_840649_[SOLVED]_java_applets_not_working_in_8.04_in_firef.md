---
title: "[SOLVED] java applets not working in 8.04 in firefox"
date: 2008-06-25
forum: General Help
---

### Post by dopple on 2008-06-25
Hi There. For some reason Java applets are not working on firefox 2. Here's the skinny
I'm running 8.04 32bit installation.
java version output
```
java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
```

when I go to about:plugins in firefox, there is no mention of any java plugins (only shockwave).

When I go into edit > prefs > content
Java is enabled.

When I access synaptic I have the following packages installed (I have also tried re-installing them)
sun-java6-jre, sun-java6-plugin, sun-java6-bin.

This is driving me nuts. I would have been blissfully ignorant of this had the missus not been trying to upload photos to bebo. :(

---

### Post by forger on 2008-06-25
edited: woops, edited out the question

ok, try this and post back the output:
```
update-alternatives --list java
```

---

### Post by dexter.deepak on 2008-06-25
did you try running your applet in "appletviewer" ?
does it run ?

---

### Post by forger on 2008-06-25
Also, does firefox 3 work?

---

### Post by avtolle on 2008-06-25
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) for some general information.

---

### Post by dopple on 2008-06-25
@dexter.deepak
It's not actually an applet I have coded. even if I go to the sun website to try to verify my installation, it doesn't work (says additional plugins are required)

@forger
I uninstalled firefox 3 after upgrading to Hardy 8.04 as firefox 3 constantly crashed due to some process being called (is this fixed now?)

@avtolle
Thanks. I'll run through that and report any new developments.

---

### Post by dopple on 2008-06-25
After reading some of the material at that link I saw that I had the following installed.
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib

I marked these for re-installation but still no joy.

---

### Post by jimbob on 2008-06-25
I have the exact same problem in Hardy Kubuntu.  Also, using FF-2, about:plugins shows that Flash is the only one I have.  They should all be there, Mplayer,DivX, etc.

---

### Post by Zorael on 2008-06-25
Owkay. From the top.

If you want to control which of Sun's Java and OpenJDK's Java is the default, perform this command in a terminal. This is only relevant for your browser applet if it *already works* and you just want to switch between the two versions. Edit: pick Sun's stuff in the menus that spawn.
```
$ for X in `ls -w1 /etc/alternatives/*java* | grep -v .gz`; do sudo update-alternatives --config $X; done
```

To get applets working if they aren't at all, please post the output of the following commands.
```
$ sudo updatedb      # will take some time and won't output anything
$ for X in `locate /usr/lib/*/plugins/*java*`; do ls -l $X; done
$ ls -l /etc/alternatives/*java* | grep -v .gz
```
Based on that output, we'll just need to perform some quick commands and it should work right away.

---

### Post by ludicrous on 2008-06-25
I have a similar problem. The only java applet that seems to work is the Sun's applet at [http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3) which is supposed to verify if you have a working installation. It works, but says I'm using an older version of the JRE, despite recently installing, and reinstalling.

*Ubuntu 8.04, 32 bit
*Firefox 3
```
$ for X in `locate /usr/lib/*/plugins/*java*`; do ls -l $X; done
lrwxrwxrwx 1 root root 45 2008-06-17 19:34 /usr/lib/xulrunner-addons/plugins/libjavaplugin.so -> /etc/alternatives/xulrunner-1.9-javaplugin.so

```

```
$ ls -l /etc/alternatives/*java* | grep -v .gz
lrwxrwxrwx 1 root root 40 2008-06-25 19:26 /etc/alternatives/java -> /usr/lib/jvm/java-6-openjdk/jre/bin/java
lrwxrwxrwx 1 root root 39 2008-06-25 19:26 /etc/alternatives/java_vm -> /usr/lib/jvm/java-6-sun/jre/bin/java_vm
lrwxrwxrwx 1 root root 42 2008-06-25 19:26 /etc/alternatives/javaws -> /usr/lib/jvm/java-6-openjdk/jre/bin/javaws
lrwxrwxrwx 1 root root 56 2008-06-25 19:26 /etc/alternatives/xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/i386/gcjwebplugin.so

```

Interestingly, java applets work fine in Opera, so btw, that might be an easy short-term workaround :)

---

### Post by jamesstansell on 2008-06-25
@ludicrous: your problem is different than the OP.  For you, try this
```

$ sudo apt-get remove icedtea-gcjwebplugin && sudo apt-get install sun-java6-plugin && sudo update-java-alternatives -s java-6-sun

```

As far as opera goes my guess is that you already have the sun-java6-plugin package installed, and somehow opera is finding it instead of the icedtea-gcjwebplugin package.

2008-07-11:
My new guess is that opera (and konquerer) may not use the plugin packages at all.  I've seen 2 recent reports that konquerer on 64-bit ubuntu is able to use the 64-bit sun-java6-jre even though there is no sun-java6-plugin for 64-bit.  Now that I think of it I think I've heard this before, and similar things about opera.

---

### Post by jamesstansell on 2008-06-25
> **dopple said:**
> Hi There. For some reason Java applets are not working on firefox 2. Here's the skinny
I'm running 8.04 32bit installation.
java version output
```
java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
```

when I go to about:plugins in firefox, there is no mention of any java plugins (only shockwave).

When I go into edit > prefs > content
Java is enabled.

When I access synaptic I have the following packages installed (I have also tried re-installing them)
sun-java6-jre, sun-java6-plugin, sun-java6-bin.

This is driving me nuts. I would have been blissfully ignorant of this had the missus not been trying to upload photos to bebo. :(

This is a known bug with Firefox 2 and java in hardy.  If you try firefox 3 update and decide to keep it then you'll have a little easier time getting java to work.

About 3 weeks ago I was able to help someone that needed to keep firefox 2, but I don't remember exactly what he had to do.  I'll look again for that post if you like.

---

### Post by ludicrous on 2008-06-25
> **jamesstansell said:**
> @ludicrous: your problem is different than the OP.  For you, try this
```

$ sudo apt-get remove icedtea-gcjwebplugin && sudo apt-get install sun-java6-plugin && sudo update-java-alternatives -s java-6-sun

```

As far as opera goes my guess is that you already have the sun-java6-plugin package installed, and somehow opera is finding it instead of the icedtea-gcjwebplugin package.

That worked, thanks!

---

### Post by forger on 2008-06-26
> **dopple said:**
> After reading some of the material at that link I saw that I had the following installed.
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib

I marked these for re-installation but still no joy.

You should remove those
```
sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
```

```
sudo update-alternatives --config java
```

Choose Sun's java (/usr/lib/jvm/java-6-sun/jre/bin/java)

then if I were you, I would reinstall the sun java packages:
```
sudo apt-get install --reinstall sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by jamesstansell on 2008-06-26
> **jamesstansell said:**
> This is a known bug with Firefox 2 and java in hardy.  If you try firefox 3 update and decide to keep it then you'll have a little easier time getting java to work.

About 3 weeks ago I was able to help someone that needed to keep firefox 2, but I don't remember exactly what he had to do.  I'll look again for that post if you like.

I looked it up anyway.  This is for getting java working with Firefox 2.

[http://ubuntuforums.org/showpost.php?p=4908417&postcount=13](http://ubuntuforums.org/showpost.php?p=4908417&postcount=13)

There have been some updates in the works to fix the firefox 2 registration problem, but not finished yet, as far as I know.

---

### Post by jimbob on 2008-06-26
I solved my problems by apt-get removing FF2, deleting the .mozilla directory in my home folder and installing FF3.  Now all the FF plugins show up in about:plugins and they all work great.

I didn't use FF3 in the beginning because it crashed regularly on youtube and other videos.  It appears that is now fixed.

---

### Post by dopple on 2008-06-27
Hi All. Sorry for the delay. Been Über busy at work. Basically I have upgraded to FF3 because the reason I down-graded to FF2 was due to the issues jimbob stated have been fixed. (and google toolbar is working!!!!)

This has resolved the java issue. I have followed forgers instructions and uninstalled the openjdk packages and installed the sun ones.

sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib

Apologies for not getting back to you all sooner and I hope you all have a great weekend.

---

### Post by jwilentz on 2008-07-11
Forger:

You solved the problem with the clean suggestions of using Terminal to configure java and reinstall the packages!!!  Now up and working in FF3 Hardy 8.04.

Thanks so much:)

---

