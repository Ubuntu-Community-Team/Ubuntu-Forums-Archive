---
title: "Help with Java RE - new to Linux"
date: 2005-09-09
forum: General Help
---

### Post by remick182 on 2005-09-09
Hey everyone!  I'm fairly new to the Linux world, and even newer to the Ubuntu community, but I'm enjoying the hell out of it!  My first major dilemma that I'm having is getting Java RE to work.
  I've downloaded and installed two different versions of Java RE, both the 1.4.2 and the newer 1.5.0.  I got them unpacked and installed in the default /usr/lib/java/... dir's and made the appropriate links in both my /usr/lib/mozilla/plugins/ and /usr/lib/mozilla-firefox/plugins folders, but when I go to the Java test page, or any other that requires it, I get the pop up on the top of the browser saying that I'm missing the needed plugin.
  What am I doing wrong?

P.S.  All of the options to use and display Java are checked in the browser as well.

---

### Post by akcanadianeh on 2005-09-09
There's great instructions at:

[https://wiki.ubuntu.com/JavaPackageBuildNewVersions](https://wiki.ubuntu.com/JavaPackageBuildNewVersions)

Here's the long and short of it... apt-get (or synaptic) java-common and java-package (from the multiverse). download the java .bin file (not the rpm.bin) from java.sun.com. 

then do the following

```
fakeroot make-jpkg *the-.bin-file-you're-using* 
```
```
sudo dpkg -i *the-.deb-file-you-just-made* 
```

then, just to test it out, 

```
java -version
```

presto! Works on both the JDK and the JRE (the JDK includes the JRE, so don't do both seperately)

---

### Post by remick182 on 2005-09-10
Thanks a lot!  That information helped out a lot.  It seems to be working just fine now.

---

