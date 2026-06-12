---
title: "Command line and most apps not working after downgrading libc6"
date: 2020-12-21
forum: General Help
---

### Post by jamespetts on 2020-12-21
I have got into some very serious problems. I upgraded from Ubuntu 18.04 to 20.04 earlier this year. This automatically upgraded Blender from 2.79 to 2.82. I need to use Blender 2.79 as a feature (the internal renderer) was removed in the upgrade from 2.7x to 2.8x. However, I had serious problems installing the old version. I could not find any instructions as to how to install 2.79 on Ubuntu 20.04, and the .deb package for it would not work: it kept failing with dependancy errors. I tried manually to fix each of them, but then came upon one which had disastrous consequences: I installed the old lib6 package from 18.04 and now nearly everything on my system is broken apart from apps (such as Firefox) that were already running when I did this.

Here is the command line output from when I attempted to do this:

```

 sudo dpkg -i ./libc6_2.27-3ubuntu1_amd64.deb
dpkg: warning: downgrading libc6:amd64 from 2.31-0ubuntu9.1 to 2.27-3ubuntu1
(Reading database ... 244437 files and directories currently installed.)
Preparing to unpack .../libc6_2.27-3ubuntu1_amd64.deb ...
De-configuring libc6:i386 (2.31-0ubuntu9.1) ...
Unpacking libc6:amd64 (2.27-3ubuntu1) over (2.31-0ubuntu9.1) ...
Replaced by files in installed package libcrypt1:amd64 (1:4.4.10-10ubuntu4) ...
dpkg: error processing package libc6:amd64 (--install):
 package libc6:amd64 2.27-3ubuntu1 cannot be configured because libc6:i386 is at a different version (2.31-0ubuntu9.1)
dpkg: error processing package libc6:i386 (--install):
 package libc6:i386 2.31-0ubuntu9.1 cannot be configured because libc6:amd64 is at a different version (2.27-3ubuntu1)
Errors were encountered while processing:
 libc6:amd64
 libc6:i386
james@macaroon:~/Downloads$ sudo apt install ./libc6_2.27-3ubuntu1_amd64.deb
sudo: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.30' not found (required by /lib/x86_64-linux-gnu/libselinux.so.1)

```

Now, almost any command that I enter in the terminal will give an error, e.g.:

```
james@macaroon:~/Downloads$ ls
ls: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.30' not found (required by /lib/x86_64-linux-gnu/libselinux.so.1)
james@macaroon:~/Downloads$ bash
james@macaroon:~/Downloads$ ls
ls: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.30' not found (required by /lib/x86_64-linux-gnu/libselinux.so.1)
james@macaroon:~/Downloads$ bash
james@macaroon:~/Downloads$ sudo
sudo: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.30' not found (required by /lib/x86_64-linux-gnu/libselinux.so.1)

```

This means that I cannot find any way of reverting the change that I have made. A few basic commands (nano, cp, rm, cd, wget) do seem to work. The GUI is no better - most apps that are not already running fail to run with no visible error message - attempting to run them simply has no effect. 

Most icons in "system settings" have no effect when clicked on. 

I am not sure how to revert to a working state given that not even the command line now works. I should be extremely grateful for any assistance.

---

### Post by Holger_Gehrke on 2020-12-21
libc is a **very** important library. Almost everything in a GNU/Linux System uses it. I think your best option is to get a bootable Flash drive with a live-system on it, back up your files and then do a fresh installation. After that you can try to either get the old version from blender.org (which might not work) or as a snap (which will work but brings the usual problems snaps have; use 'sudo snap install blender --channel=2.79/stable --classic' to get and install it).

Holger

---

### Post by jamespetts on 2020-12-21
Yes, I see the problem - everything that I need to run to perform a rescue depends on the very files that have been downgraded and are no longer compatible. I managed to get the correct version of libc6.so and libm6.so from another computer, but I cannot copy them to the correct folder to fix the installation because "sudo" and "su" do not work.

---

### Post by The Cog on 2020-12-21
> **jamespetts said:**
> YI managed to get the correct version of libc6.so and libm6.so from another computer, but I cannot copy them to the correct folder to fix the installation because "sudo" and "su" do not work.
That's a good start. I think you should be able to use a live installer to copy the files to the failed system. 
As for using the older Blender - maybe installing 10.04 in a guest VM might be the best approach?

---

### Post by TheFu on 2020-12-21
Hint:  Use a "Try Ubuntu" install environment booted from a USB flash drive.

but as others have said, you'll need format and wipe the OS.  Hopefully, your HOME and data files are in different partitions, so if you are very, very, careful, then those won't be impacted.  If you aren't 100% certain doing this, backup everything you cannot lose, disconnect the backup storage and do a full wipe-install.

libc is *THE CORE LIBRARY* for pretty much every program on any computer - Windows, Linux, BSD, Solaris, iOS, Android, WinCE, Blackberry, Nokia, Netware, AIX, Irix, SunOS, Ultrix, DigitalUnix, ... all of them. It is like a foundation to a home.

---

