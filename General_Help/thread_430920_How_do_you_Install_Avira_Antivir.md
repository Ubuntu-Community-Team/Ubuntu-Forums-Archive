---
title: "How do you Install Avira Antivir"
date: 2007-05-02
forum: General Help
---

### Post by Rich_li_ny on 2007-05-02
Although Linux viruses are not wide spread we can easily take a part in preventing them from spreading.   It's would be quite embarrassing if we are to send an email only to learn later that we passed along some malicious code to one of our friends that uses a Windows machine.   Making our our systems a little more secure and a nice added bonus.  

This afternoon I spent a great deal of time reviewing no cost Linux antivirus software. 
One of the sites I found helpful was [http://www.av-comparatives.org](http://www.av-comparatives.org)

After reading some reviews I decided the open source versions just didn't provide a high enough level of protection.   Of all the freebie anitvirus software I read up on, the two that topped the list for me were F-Prot and Avira Antivir.    After installing F-prot and playing around with it for a while I decided to uninstall it and give Avira a try.  [http://www.avira.com](http://www.avira.com).  

So now I have this file..   antivir-workstation-pers.tar.gz  and have no clue how to "properly" install it.    has anyone here tried Antivir on Ubuntu or Xubuntu?    What does it take to install this?

Also if it's a good program what would it take to ad it to the repositories so that everyone else could easily install it?

Rich

---

### Post by henkth on 2007-05-11
Hi,

I agree with you that it's a good idea to have an antivirus scanner on our linux system, so we don't send viruses to others with other operating systems, that can have adverse effects.

I have good experience with Antivir on a windows system, so I recently set it up on my linux. I found a good link that got me started, check this one out:

[http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php](http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php)

If you still have problems let me know, I'll try to walk you through the steps I took to get Antivir running.

Good luck! :) 

Henk.

---

### Post by murmelhunter on 2007-07-01
at wiki is a good guide see:

[http://wiki.ubuntuusers.de/AntiVir](http://wiki.ubuntuusers.de/AntiVir)

I'm currently have Antivir installed and can confirm that the solution is working well.

Including  the gui interface and to start it simply from the menu.

Since the stuff is in German please let me know if you need a small translation.

---

### Post by Blind Tiger on 2007-09-13
Greetings,

I am considering installing Antivir, even if just for peace of mind.  You had mentioned the possibility of a translation of the German wiki.  Is this available?  Thanks.

---

### Post by uroskriznar on 2008-02-19
Hi, I tried installing Antivir in Ubuntu Guttsy Gibbon using the following link:

[http://allyourtech.com/content/artic...untu_linux.php](http://allyourtech.com/content/artic...untu_linux.php)

I went step by step but I get this error messages:

uros6@uros6-desktop:~$ sudo rmmod capability
ERROR: Module capability does not exist in /proc/modules
uros6@uros6-desktop:~$

uros6@uros6-desktop:~$ sudo modprobe dazuko
FATAL: Module dazuko not found.
FATAL: Error inserting capability (/lib/modules/2.6.22-14-generic/kernel/security/capability.ko): Invalid argument
FATAL: Error running install command for dazuko

uros6@uros6-desktop:~$ sudo modprobe capability
FATAL: Error inserting capability (/lib/modules/2.6.22-14-generic/kernel/security/capability.ko): Invalid argument

Everything else works. I managed to get Antivir running but the guard isn't working -> 
Files per second 0 and state stopped.

Can anyone help me please and I don't speak German for the other link to help me???

---

### Post by rschu68 on 2008-03-08
In Gutsy, instead of

$ sudo rmmod capability
$ sudo insmod ./dazuko.ko
$ sudo modprobe capability

this works

$ sudo rmmod apparmor
$ sudo insmod ./dazuko.ko

[https://bugs.launchpad.net/ubuntu/+bug/118842](https://bugs.launchpad.net/ubuntu/+bug/118842)

---

### Post by 7F0C147C on 2008-07-12
I have the Avira Antivir TAR package downloaded, and I can't seem to install it. Other programs, like TrueCrypt, I just double clicked the DEB and it installed. For Flash I had to extract from the TAR, and there were detailed instructions helping a new guy, like myself, to install it.

In the TAR package, there is an install bash script that I have tried running (as normal user, sudo, and root) but it does nothing.

I do not wish to tinker with the DEB package lists, yet. ***How do I get this ball rolling?***

Kubuntu 8.04 Hardy Heron

EDIT (1): accidentally mistaken TAR archives as DEB packages. Still have a problem though.
EDIT (2): typed the wrong Kubuntu version

---

