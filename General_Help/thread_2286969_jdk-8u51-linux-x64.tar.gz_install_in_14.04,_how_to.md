---
title: "jdk-8u51-linux-x64.tar.gz install in 14.04, how to ?"
date: 2015-07-16
forum: General Help
---

### Post by diliptmc on 2015-07-16
I download from [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

Tried

1. Unzipped and tried **make** command after entering the folder and opening it inside Terminal. Nothing worked. 

Tried 

2. ```
tar -xzf jdk-8u51-linux-x64.tar.gz
```  in download folder
Everything in Google says 

> cd archive-name
./configure
make
sudo make install



as a way to install tar.gz files. But a bit of helping had can really help because there is no configure.sh in the folder or when I open uncompressed folder in Terminal and use .```
/configure 
```or ```
make
``` commands, nothing happens.

---

### Post by dino99 on 2015-07-16
do you have followed the instructions given with the link above ?

---

### Post by monkeybrain20122 on 2015-07-16
Don't have to compile it. Just install from a ppa [https://launchpad.net/~webupd8team/+archive/ubuntu/java?field.series_filter=trusty](https://launchpad.net/~webupd8team/+archive/ubuntu/java?field.series_filter=trusty)

You need to set your java default afterwards. Install galaternatives from repo and pick your java default from the gui.

---

### Post by meetdilip on 2015-07-16
> **dino99 said:**
> do you have followed the instructions given with the link above ?

Yes.

---

### Post by meetdilip on 2015-07-16
> **monkeybrain20122 said:**
> Don't have to compile it. Just install from a ppa [https://launchpad.net/~webupd8team/+archive/ubuntu/java?field.series_filter=trusty](https://launchpad.net/~webupd8team/+archive/ubuntu/java?field.series_filter=trusty)

You need to set your java default afterwards. Install galaternatives from repo and pick your java default from the gui.

I am on with the install commands given in the link. Sadly, I am not using a high speed connection and it is stuck in the middle. It would be great to have commands which I use to make the downloaded package work.

---

### Post by meetdilip on 2015-07-16
@monkeybrain20122

Thanks, the link worked. :)

Download complete now

```
myname@Ubuntu1:~$ java -version
java version "1.8.0_45"
Java(TM) SE Runtime Environment (build 1.8.0_45-b14)
Java HotSpot(TM) 

```

---

### Post by gnwiii on 2015-07-18
The link did not work!.  You said you wanted to install jdk-8u51-linux-x64, which is the current version.  You have the old version ("1.8.0_45").   It looks like the web8team PPA is not being maintained, so 
still has an old version.

You can install the current JDK manually following the basic outline from [http://maciek.hubpages.com/hub/Ubuntu-Install-Sun-Java-Alternativeshttp://]("http://maciek.hubpages.com/hub/Ubuntu-Install-Sun-Java-Alternativeshttp://").  

## Download [FONT=Fixedsys]jdk-8u51-linux-x64.tar.gz[/FONT] from Oracle.

## extract into `/usr/lib/jvm`

## create symbolic link

[FONT=Fixedsys]
    $ sudo ln -s jdk1.8.0_51 java-8-oracle
[/FONT]

## If it is not already present from a previous install, create `.java-8-oracle.jinfo`

You can use the openjdk .jinfo file as a template.  I set the priority to 1102.  The 
plugin line is:

[FONT=Fixedsys]
plugin mozilla-javaplugin.so /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnpjp2.so
[/FONT]

##  register new alternatives in update-alternatives mechanism.

[FONT=Fixedsys]

    $ cat .java-8-oracle.jinfo | grep -E '^(hl|jre|jdk)' | \
	awk '{print "/usr/bin/" $2 " " $2 " " $3 " 1102 \n"}' | \
	xargs -t -n4 sudo update-alternatives --verbose --install

    $ sudo update-alternatives --verbose --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnpjp2.so 30
[/FONT]

## enable

[FONT=Fixedsys]
    $ sudo update-java-alternatives -s java-8-oracle

    $ java -version
	java version "1.8.0_51"
	Java(TM) SE Runtime Environment (build 1.8.0_51-b16)
	Java HotSpot(TM) 64-Bit Server VM (build 25.51-b03, mixed mode)
[/FONT]

---

### Post by SuperFreak on 2015-07-19
Getting stuck at
> ## register new alternatives in update-alternatives mechanism.

Doesn't seem to update java

---

### Post by jcllings on 2015-08-07
What I've noticed is that the JVM is updated but no JDK is installed.

---

### Post by QIII on 2015-08-07
That's a lot of unnecessary work.

The easiest way to install Oracle Java 8, JRE and JDK, is to use the [webupd8 method]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

Andrew updates the scripts as new Java releases come out, and since it's in a PPA that you have added, you get the new updates when you do your normal updates.  No extra work. 

If you install as described in the first post, you have to watch for updates and reinstall them every time.

---

### Post by leoexcelsus on 2015-08-15
I was also facing this java update problem. Indeed, the easiest way of doing so is using the webupd8.org ppa, but for some reason I didn't have this ppa anymore in my software sources. Somehow it was automatically removed. After I realized the absence of the ppa, I just added it again and got the update through "sudo apt-get update". I hope this message helps others with the same issue.

---

