---
title: "[SOLVED] Uhh... Java/bash weirdness"
date: 2007-07-18
forum: General Help
---

### Post by jw5801 on 2007-07-18
I'm trying to run a note-taking program called "[Jarnal](http://www.dklevine.com/general/software/tc1000/jarnal.htm)" which I installed from a .deb on that link, however when I try to run it I get the following:```
jw5801@jw5801-laptop:~$ jarnal
/usr/bin/jarnal: line 17: java: command not found
```
So I then tried:
```
jw5801@jw5801-laptop:~$ java
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
jw5801@jw5801-laptop:~$ sudo apt-get install j2re1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
j2re1.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```
and now I'm just confused!

---

### Post by Boobek on 2007-07-18
try this, but its just a  tip...:
sudo dpkg-reconfigure java

---

### Post by jw5801 on 2007-07-18
Nah, that returned a similar error. Tried it on the package containing java as well:
```
jw5801@jw5801-laptop:~$ sudo dpkg-reconfigure java
Password:
Package `java' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: java is not installed
jw5801@jw5801-laptop:~$ sudo dpkg-reconfigure j2re1.4
jw5801@jw5801-laptop:~$ java
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
```
Also for the record I tried a couple of the other packages listed there with no difference.

---

### Post by ThrobbingBrain66 on 2007-07-18
Do you have the universe and multiverse repos enabled?

Check in System>Administration>Software Sources and make sure that these two are enabled.

then in a terminal type ```
sudo apt-get update
```
finally ```
sudo aptitude install sun-java6-bin
```

EDIT: This link gives a good howto on installing java and updating alternatives. Section 4 and 6 are what's relevant to you
[https://help.ubuntu.com/community/Java#head-7852ba79216c811b4345924d824bf15489ce7164](https://help.ubuntu.com/community/Java#head-7852ba79216c811b4345924d824bf15489ce7164)

---

### Post by jw5801 on 2007-07-18
:oops:
My bad. I did have sun-java installed, but I couldn't get the firefox plugin to be recognised (64-bit) so I installed blackdown java (j2re1.4-mozilla-plugin) as it works for 64-bit. I must have decided I didn't need the sun version after I did that. Any idea why I was being pointed to packages that didn't contain the command I was after?

---

