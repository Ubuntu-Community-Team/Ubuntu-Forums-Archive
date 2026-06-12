---
title: "Can't Find Proftpd Package on Edgy Server Edition"
date: 2006-11-07
forum: General Help
---

### Post by louie55 on 2006-11-07
I just installed Ubuntu 6.1 Edgy Eft SERVER Edition, not the desktop edition. I have made no changes to the sources.list file other than commenting out the CDROM line. I type the following command:

```
sudo apt-get install proftpd
```

And get this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package proftpd
```

Any ideas as to why it can't find it?? Is this something special for the Server edition??

Here is my sources.list:

```
#
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


#deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

Thanks.

Louie

---

### Post by louie55 on 2006-11-07
Also, it can not find the PHPMyAdmin package.

This is supposed to be a server edition. It doesn't make much sense to install a server edition and then not be able to install other server applications from the internet out of the box. Anybody agree??

Also, in case you were wondering, I did do "sudo apt-get update" before I tried installing these.

Thanks.

Louie

---

### Post by louie55 on 2006-11-07
Ok, I got it to work by uncommenting the "Universe" repository line in sources.list. Why is this commented by default?? Is there any reason I should recomment it when I'm done??

Thanks.

Louie

---

### Post by OwenA on 2006-11-11
If you uncomment those lines you still need to access the internet correct? Or will it impact what is already on your harddrive?

---

