---
title: "TrueCrypt 4.2a over Kubuntu 6.10"
date: 2006-12-17
forum: General Help
---

### Post by Technical on 2006-12-17
I was reading this thread:
[http://ubuntuforums.org/showthread.php?t=269305](http://ubuntuforums.org/showthread.php?t=269305)

I did this:
```
apt-get install linux-source
apt-get install build-essential
apt-get install build-essential
apt-get install dmsetup
cd /home/tech/Download/Applications/Truecrypt/truecrypt-4.2a-build/Linux
sudo ./install.sh
<Checking installation requirements...>
<Testing truecrypt... Done.>
<Installing kernel module... Done.>
<Installing truecrypt to /usr/bin... Done.>
<Installing man page to /usr/share/man/man1... Done.>
<Installing user guide to /usr/share/truecrypt/doc... Done.>
<Installing backup kernel module to /usr/share/truecrypt/kernel... Done.>
```

When I try to mount the volume, I get this
```
truecrypt /dev/hdb6 /mnt/tc
<password>
Invalid module format
truecrypt: Failed to load TrueCrypt kernel module
```

Can anybody help? I cannot use TrueCrypt with Kubuntu 6.10.
Many thanks. :cool:

---

### Post by Technical on 2006-12-22
No one for helping me? :-#

---

### Post by ariel on 2006-12-22
I'm new to truecrypt, I'm just wondering why you have to use an install script instead of the deb? they seem to offer the debs in their download page

---

### Post by Technical on 2006-12-26
> **ariel said:**
> I'm new to truecrypt, I'm just wondering why you have to use an install script instead of the deb? they seem to offer the debs in their download page

Well, I don't have to use a script to install TrueCrypt.
The deb package seems to work.
But, when I try to use TrueCrypt:

```
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.17.ko': -1 Invalid module format
FATAL: Error inserting truecrypt (/lib/modules/2.6.17-10-386/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module

```

So, unable to install a kernel module... I've tried other solution.
But what I can see is there I won't find that much help in this forum... :-k

---

### Post by flyingbrass on 2006-12-26
Did you set up the kernel source?  Go to the /usr/src directory.  You'll see a file linux-source-whatever.tar.bz2.  If you don't have a linux-source-whatever directory, you need to:

tar xjvf linux-source-whatever.tar.bz2

Then create a symlink:

ln -s linux-source-whatever linux

Obviously, replace "whatever" with your kernel version numbers.  

I'd locate and delete all the truecrypt files previously installed (first remove the deb if you have it installed), and then reinstall using the script.  To find the files:

locate truecrypt

I've had trouble with the truecrypt deb even in Dapper, probably because I run a 686 kernel.  It will install, but the module isn't right and won't load.  Use the script.

---

### Post by Technical on 2006-12-29
```
# sudo ./install.sh
Checking installation requirements...
Checking build requirements...
Linux kernel (2.6.17-10-386) source directory [/usr/src/linux]: /usr/src/linux-2.6.17.10/
Building internal kernel modules (may take a long time)... Done.
Building kernel module... Done.
Building truecrypt... Done.
Testing truecrypt... Done.

Install binaries to [/usr/bin]:
Install man page to [/usr/share/man]:
Install user guide and kernel module to [/usr/share/truecrypt]:
Allow non-admin users to run TrueCrypt [y/N]: y
Installing kernel module... Done.
Installing truecrypt to /usr/bin... Done.
Installing man page to /usr/share/man/man1... Done.
Installing user guide to /usr/share/truecrypt/doc... Done.
Installing backup kernel module to /usr/share/truecrypt/kernel... Done.

# truecrypt /dev/hdb6 /mnt/tc
Enter password for '/dev/hdb6':

insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.17.ko': -1 Unknown symbol in module
FATAL: Error inserting truecrypt (/lib/modules/2.6.17-10-386/extra/truecrypt.ko): Unknown symbol in module, or unknown parameter (see dmesg)
truecrypt: Failed to load TrueCrypt kernel module

```

As you can see, still unhappy... _Failed to load TrueCrypt kernel module_...
I don't know what can I do more :(

---

### Post by nashjc on 2007-04-02
For what it's worth, I'm getting the same msg with Edgy (Gnome interface) on Truecrypt 4.3. The .ko module is present, but seems to be corrupt. 

Truecrypt folk seem not terribly interested in Linux users. For me it is critical to have multi-platform functionality.

Prof. J C Nash

---

### Post by Technical on 2007-04-02
> **nashjc said:**
> For what it's worth, I'm getting the same msg with Edgy (Gnome interface) on Truecrypt 4.3. The .ko module is present, but seems to be corrupt. 

Truecrypt folk seem not terribly interested in Linux users. For me it is critical to have multi-platform functionality.

Prof. J C Nash
Yeah... it's a pity.
Not only there is a lack of support but also a delay: we're almost on Ubuntu Feisty (version 7) and they're on early Edgy... worse, the .ko module is always missed... I think it will be possible to use TrueCrypt with Kubuntu but, after all my tests and patience I couldn't manage it.
Anyway, thanks for posting.

---

### Post by kinoini on 2007-04-09
Hey guys.  I had similar problems with truecrypt 4.3, though I'm not using ubuntu.  If you've succesfully installed truecrypt, but get the "Invalid module format" it's likely because of a difference in your vermagic values.  Quick and dirty way to check your vermagic value for your running kernel is this code:

root@localhost /]# modinfo /lib/modules/`uname -r`/kernel/kernel/intermodule.ko.gz
filename: /lib/modules/2.6.17.14-mm-desktop-5mdvsmp/kernel/kernel/intermodule.ko.gz
license: GPL
srcversion: B9B3C867A7C9E13DBA0E8C5
depends:
vermagic: 2.6.17.14-mm-desktop-5mdvsmp SMP preempt mod_unload 686 gcc-4.1

Then check your vermagic value for the truecypt.ko fiile

[root@localhost Linux]# modinfo /lib/modules/`uname -r`/extra/truecrypt.ko
filename:       truecrypt.ko
author:         TrueCrypt Foundation
description:    device-mapper target for encryption and decryption of TrueCrypt volumes
license:        GPL and additional rights
vermagic:       2.6.17.14-mm-desktop-5mdvsmp SMP preempt mod_unload 686 gcc-4.1
depends:
srcversion:     61993AB36305CF1F8082002
parm:           trace:Trace level (int)

If the vermagic values are the same, you shouldn't have a problem, but since you're having a problem, they probably aren't.

The truecrypt build.sh looks in /usr/src for your source code, not in /lib/modules, even though it writes out the truecrypt.ko file in /lib/moduels.

So:
Make sure that your source code is *really* your source code, and that it's in /usr/src, or a symlink in /usr/src points to the correct location.  Check out the .config file in /usr/src/yourversion/.confg and compare it to the file in /boot/config-`uname -r`.  If they don't match, you'll have a problem with running truecrypt.  Find out if you really have the right source code, or if you have a "master" source that was used to build a few versions of kernels.

Make sure that the Makefile in /usr/src/yourversion matches the uname -r for your kernel.

more /usr/src/kernel-multimedia-2.6.17.14-5mdv/Makefile
VERSION = 2
PATCHLEVEL = 6
SUBLEVEL = 17
EXTRAVERSION = .14-5mdvmmcustom

Compare that to uname -r.  If you come up with something like 2.6.17.14-mm-desktop-5mdvsmp, then its the wrong Makefile.  If all else matches you can edit the Makefile and set the EXTRAVERSION to the correct value.

If nothing matches, you probably have the wrong source.

Check out this quick doco - Chapter 2.8 - that gives a good outline of ways to fix this.  [http://www.openaddict.com/documents/lkmpg/index.html](http://www.openaddict.com/documents/lkmpg/index.html)

There is also a thread over on club mandriva, where I struggeled my through getting truecrypt to work.  Thanks to Danny over there who is enormously patient, and a good sport.

But we got it to work, and I'm reasonably comfortable I understand why.
[http://forum.club.mandriva.com/viewtopic.php?t=62940&postdays=0&postorder=asc&start=0&sid=b0decedfb601d5ac435be849634a9ae5](http://forum.club.mandriva.com/viewtopic.php?t=62940&postdays=0&postorder=asc&start=0&sid=b0decedfb601d5ac435be849634a9ae5)

k~~~

---

