---
title: "Where is the local kernel source tree?"
date: 2007-12-31
forum: General Help
---

### Post by ender42 on 2007-12-31
Trying to get dialup working, using scanModem.gz kinda directed me to download and use slmodemd, finally got that transferred (why won't my floppy work?? whatever...)

From the output of: tar -xvvf SLMODEMD.gcc3.tar --> README:

> Default KERNEL_DIR is '/lib/modules/<kerne-version>/build'. Many
> Linux Distributions use directory '/usr/src/linux-<version>' also.

/lib/modules/2.6.10-5-386/ <-- has no build/ directory or build file, just boot/, initrd/, and kernel/ directories, and 9 files:  modules.*

/lib/modules/2.6.10-5-386/kernel/ <-- is this the 'local kernel source tree'??


/usr/src/ <-- only has an rpm/ directory available

/usr/src/rpm/ <-- has several directories, among them the best-looking bet is:

/usr/src/rpm/SOURCES/ <-- which is an empty directory


So, should I be making my KERNEL_DIR point to /lib/modules/2.6.10-5-386/kernel/, or somewhere else?

---

### Post by nick_h on 2007-12-31
Kernel sources are not installed by default in Ubuntu.  If you download a kernel source package it places a linux-source-x.y.zz.tar.bz2 file in /usr/src which is where you could extract it to.

---

### Post by ender42 on 2007-12-31
Well, it says that in many cases I will need the correct path to my local kernel source tree in order to have a correct makefile - which I need so that I can make the drivers/program or whatever this is in order to get my modem up and running.

Should I point it to an empty directory (and which directory should I use?)?  Or do I need to download some sources to put into the directory in question?

And you're telling me that I should be putting the SLMODEMD directory (which I untarred on my desktop - since I moved it from a memory card (it didn't want to copy correctly from a floppy), because there's no internet connection on that machine), into /usr/src, eh?

---

### Post by nick_h on 2007-12-31
I do have a build directory under /lib/modules/<version>.  If it needs the full kernel source then you will need to install it.  By default it will install under /usr/src

---

### Post by ender42 on 2007-12-31
Are you saying that you have?:
/lib/modules/<version>/build/

And are you using 2.6, or something else?

---

### Post by tgilber1 on 2007-12-31
Linux modules are in the directory:  /lib/modules/`uname -r`

Linux src files are in the directory:  /usr/src/linux-headers-`uname -r`


To install the Linux source files:

 sudo apt-get install linux-headers-`uname -r`

---

### Post by ender42 on 2007-12-31
Yeah, wasn't asking about modules - I can use modprobe, and it does mostly what I want.  But I was trying to get a clarification on what this README was trying to tell me, because I have no idea what the phrase 'local kernel source tree' means, or where it's suppossed to be located on my machine...

Appears I don't have Linux src files (as is obvious above), and no I can't get them the way you recommend (apt-get or aptitude), becuase the machine isn't on the net (which is what I'm trying to fix...)

---

### Post by nick_h on 2007-12-31
> Are you saying that you have?:
/lib/modules/<version>/build/
Yes, but my kernel source is not located there.

I installed the package linux-source-2.6.20 and it placed a tar in /usr/src.  I think most people extract it there into /usr/src/linux-source-2.6.20 and then make a symbolic link /usr/src/linux to it.  I actually extracted it to my home directory and compiled it there.

---

### Post by tgilber1 on 2008-01-05
I think it's best to install linux source files into the user's home directory, thereby avoiding any conflict and mistakes.

[LIST=1]
[*]cd ~
[*]mkdir src
[*]cd src
[*]pwd # should show /home/<user>/src - e.g., /home/johndoe/src
[*]sudo apt-get install linux-source
[*]tar -xjvf linux-source-<version>
[*]cd  ~/src/linux-source-<version>, e.g., /home/johndoe/src/linux-source-2.6.22
[*]pwd #verifies that you are in your home's sub-directory src
[*]cp -vi /boot/config-<kernel-version> ./config #e.g., cp -vi /boot/config-2.6.22-14-generic ./config
[*]If applicable, apply kernel patch
[*]make menuconfig # to make changes to the kernel
[*]make-kpkg --rootcmd fakeroot --initrd --append-to-version=-**<custom>** 
ex. kernel-image kernel-headers #e.g., make-kpkg --rootcmd fakeroot --initrd --append-to-version=-mybackup kernel-image kernel-headers

Make sure that you leave the - after the equal = sign of append-to-version

[*]cd .. # change one level up to view new kernel.deb packages

Note:  Beware if you're using restricted drivers, there will be additional work

[/LIST]

Reference:  [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

