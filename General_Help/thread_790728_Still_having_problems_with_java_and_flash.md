---
title: "Still having problems with java and flash"
date: 2008-05-11
forum: General Help
---

### Post by carl99fan on 2008-05-11
1. How do I uninstall everything that is Java and Flash?

2. What is the correct method and sequence for uninstalling Java and Flash for Ubuntu 8.04?

3. What is the correct method and sequence for installing (or re-installing) Java and Flash for Ubuntu 8.04?

I tried a lot of different methods for correcting my issues, but what I think has happened is that I tried too many. It seems the suggestions I tried, although helpful, have not corrected the problems I am still encountering.
After I have correctly installed these programs and resolved my Java and Flash issues, I then want to install restricted-extras. I want to be able to view streaming video on my favorite sites (NASCAR.com, etc.), use Dizzler and  Flash-driven chat boxes. Thank you in advance for any help and/or suggestions!

---

### Post by carl99fan on 2008-05-11
Is this not the right thing to ask? I am lost here. I also downgraded my Mozilla to 2.0 is that hurting me?

---

### Post by jturnbul on 2008-05-11
I think Im having the same problems.  Worst move I could have ever done was to upgrade.  Things were running perfectly.  Better then any windows maching Ive had.  Now it feels like I stepped back 5-6 years in the world of linux, where video, flash, and java take forever to get worked out

---

### Post by lovepoker0987 on 2008-05-11
Im having problems too. I am a brand new user, just installed ubuntu and upgraded to 8.04 today and I really like everything except the fact that I am new and having problems with flash and java. Hope someone follows this up, I have searched the forums and tried different things and am thinking I am only making the problem worse.

Thanx.

---

### Post by drs305 on 2008-05-11
To remove java:
```
sudo apt-get purge flashplugin-nonfree
```

For removing java, there are various versions. It might be best to open synaptic, click on the search button at the top right, and search for java. There are sun and icedtea versions of java, as well as openjdk.

Are you using a 64 bit AMD installation? If so, there are excellent guides in the 64 bit users forum? Java still doesn't work natively in 64 bit, you must use a 32 bit browser.

AMD 64 Flash: 
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

AMD 64 Java w/ 32 bit Firefox: [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by carl99fan on 2008-05-11
> **drs305 said:**
> To remove java:
```
sudo apt-get purge flashplugin-nonfree
```

For removing java, there are various versions. It might be best to open synaptic, click on the search button at the top right, and search for java. There are sun and icedtea versions of java, as well as openjdk.

Are you using a 64 bit AMD installation? If so, there are excellent guides in the 64 bit users forum? Java still doesn't work natively in 64 bit, you must use a 32 bit browser.

AMD 64 Flash: 
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

AMD 64 Java w/ 32 bit Firefox: [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)
I get this message....

This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

Is in uninstalled now?
I don't get it. I thought I din not need on download anything.. I think mine is a mess :(

---

### Post by drs305 on 2008-05-11
Okay, open synaptic, scroll in the right pane to 'flashplugin-nonfree'. If it is installed, it should have a green box. Right click, select Mark for complete removal, and then click on the apply at the top of the synaptic window.

I think you could also try to remove it via terminal with the following but personally I'd just go to synaptic for now.

```
sudo apt-get -f purge flashplugin-nonfree
```

---

### Post by carl99fan on 2008-05-11
OK I keep having problems now... When ever I try to go to the synaptac manager I am told to do the following: dpkg --configure -a
  So I do it and I I get this:
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
How do I clear this stuff out and get to work on this?
It all started when Frostwire stopped working and I uninstalled it and reinstalled.
I am still lost here. Last night I downloaded stuff and then a forum user told me I should not have to download any files from a website.....

---

### Post by drs305 on 2008-05-11
Okay then, try this to remove the -doc package:
```
sudo apt-get remove sun-java6-doc
```

---

