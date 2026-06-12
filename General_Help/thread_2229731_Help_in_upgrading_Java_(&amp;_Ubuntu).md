---
title: "Help in upgrading Java (&amp; Ubuntu)"
date: 2014-06-14
forum: General Help
---

### Post by sarahfoxnz on 2014-06-14
Upgrading Ubuntu & Java.

Priority 1 query: Java

Priority 2: Ubuntu.


1. Java.

on a particular website ( savevid.com ) I am getting an error - telling me to upgrade my Java.

EDIT: In Nov 2013, my java did work on this website

> 
Java&#8482; Plugin required

In order to download videos, you must install the Java&#8482; Plugin


What I have done so far :-


> 
sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1051      manual mode



(version 7 does not seem to have an AUTO mode ?)


> 
file /etc/alternatives/java /etc/alternatives/javac

/etc/alternatives/java:  symbolic link to `/usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java'
/etc/alternatives/javac: symbolic link to `/usr/lib/jvm/java-6-openjdk-amd64/bin/javac'



> 
 file `which java javac`

/usr/bin/java:  symbolic link to `/etc/alternatives/java'
/usr/bin/javac: symbolic link to `/etc/alternatives/javac'


QUESTION: What is the easiest / command-lines i can use to get the latest Java running ?


2. UBUNTU:

I am currently running LTS 12:04
Release 12.04 (precise) 64-bit

GNOME 3.4.2

Query: when is the next release / version going to be ? (from past experience, its been every 1-2 years)

Is 12:04 currently supported ?

---

### Post by claracc on 2014-06-15
I recommend you read the information in this page: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java), I would select the webup8 method : [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) to install java, which is the most easy one and receive updates automatically.

The current release is ubuntu 14.04 a long term support one, but of course ibuntu 12.04 is still supported and as it is a long term support one too, you will receive security updates for it till 2017.

Please, see: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

