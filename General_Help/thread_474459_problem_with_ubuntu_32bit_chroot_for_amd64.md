---
title: "problem with ubuntu 32bit chroot for amd64"
date: 2007-06-15
forum: General Help
---

### Post by Irti on 2007-06-15
i was trying to install opera for 64 bit amd using this method but i had problems with step 3 and 4........i somehow managed to get past the 3rd step...but then in the 4rth step...debootstrap just wont invoke...can anyone plzzz help me........the original documentation is at this site......[http://process-of-elimination.net/wiki/Ubuntu_32bit_CHROOT_for_AMD64](http://process-of-elimination.net/wiki/Ubuntu_32bit_CHROOT_for_AMD64)

this is what comes up

irti@irti-Linux:~$ debootstrap --arch i386 $feisty $chroot32
I: usage: [OPTION]... <suite> <target> [<mirror> [<script>]]
I: Try `debootstrap --help' for more information.
E: You must specify a suite and a target.
irti@irti-Linux:~$ 



Ubuntu 32bit CHROOT for AMD64
From Process of Elimination
[edit]
Introduction

This document is a work-in-progress explicating the steps for setting up a 32bit chroot environment in the middle of an AMD64 install. It is particularly useful in situations in which one might want to run native 32bit software such as Opera or Wine.
[edit]
Procedure

   1. apt-get install dchroot debootstrap
   2. Choose a location that has ample free space (e.g., /usr/chroot32), and invoke mkdir /usr/chroot32.
   [COLOR="Red"]3. Add that location, $CHROOT32, to /etc/dchroot.conf in the form of $UBUNTURELEASENAME $CHROOT32, where $UBUNTURELEASENAME = {'breezy', 'hoary', 'warty'}.
   4. Invoke debootstrap --arch i386 $UBUNTURELEASENAME $CHROOT32[/COLOR].
   5. Add the following lines to $CHROOT32/etc/apt/sources.list:
         1. deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) $UBUNTURELEASENAME main restricted universe multiverse
         2. deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) $UBUNTURELEASENAME-security main restricted universe multiverse
         3. deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) $UBUNTURELEASENAME-backports main restricted universe multiverse 
   6. Invoke chroot $CHROOT32 and dpkg-reconfigure locales.
   7. Invoke apt-get update and apt-get dist-upgrade.
   8. Outside of the chroot environment, edit the main system's /etc/fstab, adding the following lines:
         1. /home $CHROOT32/home none bind 0 0
         2. /tmp $CHROOT32/tmp none bind 0 0
         3. /dev $CHROOT32/dev none bind 0 0
         4. /proc $CHROOT32/proc none bind 0 0
         5. /etc/passwd $CHROOT32/etc/passwd none bind 0 0
         6. /etc/shadow $CHROOT32/etc/shadow none bind 0 0
         7. /etc/group $CHROOT32/etc/group none bind 0 0
         8. /etc/sudoers $CHROOT32/etc/sudoers none bind 0 0
         9. /etc/hosts $CHROOT32/etc/hosts none bind 0 0
        10. /etc/resolv.conf $CHROOT32/etc/resolv.conf none bind 0 0
        11. /etc/nsswitch.conf $CHROOT32/etc/nsswitch.conf none bind 0 0
        12. For all entries in /media, perform a binding step similar to the ones above. 
   9. Invoke mount -a.
  10. Create a script, $SCRIPT, that contains the following lines:
         1. #!/bin/sh
         2. /usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*" 
  11. Invoke chmod +x $SCRIPT

---

### Post by esekyavuz on 2007-06-24
You're close!

I believe you should substitute the following way

feisty for $UBUNTURELEASENAME

and

/usr/chroot32 for $CHROOT32

Obviously, this depends on what release you're using and where you decided to set up your chroot. 

So you drop the $ entirely, and use the complete pathname for the chroot directory.


I am following this guide as well. I have a problem with

dpkg-recondifigure locales

which gives me an error 

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory



I'm able to get the chroot going (at least I think I am) but can't get apt working. It can't resolve archive.ubuntu.com although it pings fine.

Maybe you've progressed since you posted this a week ago and can give me help!

---

### Post by esekyavuz on 2007-06-25
it finally occurred to me that when I ping archive.ubuntu.com I get the IP address. So I just substituted that for the URL in etc/apt/sources.list and hey presto. Only took me 12 hours to think of that!

---

