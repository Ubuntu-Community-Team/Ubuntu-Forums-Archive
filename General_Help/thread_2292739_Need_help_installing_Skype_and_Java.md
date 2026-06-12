---
title: "Need help installing Skype and Java"
date: 2015-08-30
forum: General Help
---

### Post by darien2 on 2015-08-30
Okay so hello guys. :)

Today I installed Ubuntu, and I'm just really confused on how to install programs and things of that nature.

I've been trying to install Skype and Java for the past 4 hours, looking at countless tutorials etc, but to no prevail.

Could anyone just walk me through on the steps and possibly guide me through if I encounter errors, etc?

Thanks.

---

### Post by grahammechanical on 2015-08-30
You should title your thread "How to install skype." Then those of us with specific knowledge will know what it is you are looking for help for.

Ubuntu is Free and Open Source Software (FOSS). Skype may be free to download but it is closed source or prorietary software. Therefore access to proprietary software has to be enabled by the user. You need to enable the Partners repositories and then check for updates and then you should find Skype in the Ubuntu Software Centre.

Go to System Settings>Software & Updates>Other Software tab and enable the Ubuntu Partners repository. And then check for updates so that the Partner repositories are included in the system's list of software sources. You should then be able to find Skype in the Software Centre.

Regards.

---

### Post by monkeybrain20122 on 2015-08-30
Search for  java in synaptic/Software Centre OpenJDk will turn up, install that and also icedtea-plugin which is the java web plugin. The repo version is openjdk7 which is old but should be good for most use. If you need openjdk8 or Oracle java8 post back and we will help you to do that.

---

### Post by darien2 on 2015-08-30
> **monkeybrain20122 said:**
> Search for  java in synaptic/Software Centre OpenJDk will turn up, install that and also icedtea-plugin which is the java web plugin. The repo version is openjdk7 which is old but should be good for most use. If you need openjdk8 or Oracle java8 post back and we will help you to do that.

[IMG]http://i.imgur.com/fBQkSmr.png[/IMG]

This is what I get when I try to install OpenJDK. That little white/orange box goes back and forth, and doesn't stop.

---

### Post by monkeybrain20122 on 2015-08-30
Well I don't use the Software Centre and can't help you troubleshoot it. I would suggest installing synaptic and use it to manage your packages. Close your USC. Then in the terminal run
```
sudo apt-get install synaptic
```
Then use synaptic to install openjdk and other packages you need.

---

### Post by darien2 on 2015-08-30
Okay I tried to do that;

Opened Terminal, typed it in, gave this to me:

```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by monkeybrain20122 on 2015-08-30
You have to close the Software Centre first. Only one instant of apt-get can run at a time. The USC and synaptic are both gui frontend of the same thing (but synaptic is a lot faster and have much better search options)

---

### Post by darien2 on 2015-08-30
I was installing Java, and the download completed, but I ended with this error:

```

Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-7u80-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing package oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer

```

---

### Post by Vladlenin5000 on 2015-08-30
Actually he should wait for the update process running in the background to finish. Apt-get was already running when the user tried to install openjdk in USC.

---

### Post by CharlesA on 2015-08-30
> **darien2 said:**
> I was installing Java, and the download completed, but I ended with this error:

```

Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-7u80-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing package oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer

```

I have merged your threads. Not sure if you indented to make a new post or new thread, but it was related to your original thread.

As far as that error goes. It won't install the package because it was unable to verify it was intact.

Try running apt-get update before trying to install java.

---

### Post by monkeybrain20122 on 2015-08-30
Where exactly did you get Oracle java and how did you try to install it? I think they only provide rpm packages and tarballs Easy way is to use webupd8 ppa [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.htm](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.htm)

---

### Post by darien2 on 2015-08-30
Thank you to whomever helped, this has been resolved. :)

---

### Post by Crackers.sl on 2015-09-06
I just installed Skype and it went a treat
I took the advise from another source by typing In a terminal (For those following from Win10 and like me a newbie) 
to get a terminal press
ctrl alt t
 then type in 
   sudo apt-get install skype

---

