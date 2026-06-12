---
title: "apt-get broken"
date: 2017-10-10
forum: General Help
---

### Post by eugenio.myles on 2017-10-10
I am currently running Ubuntu 16.04.2 LTS.
I have the following issue when I try to update, upgrade, or install anything via apt-get.

```

$ sudo apt-get update
apt-get: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory

```

I attempted the following:
```

$ sudo dpkg -i ~/Downloads/apt_1.0.1ubuntu2.17_amd64.deb 
dpkg: warning: downgrading apt:i386 from 1.2.15ubuntu0.2 to 1.0.1ubuntu2.17
dpkg: warning: files list file for package 'libapt-pkg5.0:amd64' missing; assuming package has no files currently installed
(Reading database ... 192989 files and directories currently installed.)
Preparing to unpack .../apt_1.0.1ubuntu2.17_amd64.deb ...
Unpacking apt (1.0.1ubuntu2.17) over (1.2.15ubuntu0.2) ...
dpkg: dependency problems prevent configuration of apt:
 apt depends on libapt-pkg4.12 (>= 0.9.16); however:
  Package libapt-pkg4.12 is not installed.
 libapt-pkg5.0:i386 (1.2.15ubuntu0.2) breaks apt (<< 1.1~exp14) and is unpacked but not configured.
  Version of apt to be configured is 1.0.1ubuntu2.17.
 libapt-pkg5.0:amd64 (1.2.20) breaks apt (<< 1.1~exp14) and is broken due to postinst failure.
  Version of apt to be configured is 1.0.1ubuntu2.17.

dpkg: error processing package apt (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 apt

```
So no luck in re-installing apt directly...


Thanks,

Paul
,

---

### Post by Impavidus on 2017-10-10
I've difficulty seeing if that's the 32 bits or 64 bits version of Ubuntu you use. Can you enlighten me?

Your error message shows that apt cannot find a shared library, libz.so.1. This is a library that's used by a lot of applications on your Ubuntu system. An awful lot of applications, except that libz.so.1 isn't the actual library, but a symlink to the actual library, which has a more detailed version number in its name. On Ubuntu 16.04, that would be libz.so.1.2.8. Reinstalling zlib may do the trick. The actual package is called **zlib1g**. Or maybe just restoring the symlink is enough. I wonder how it could have disappeared. Show this:```
ls -l /lib/x86_64-linux-gnu/libz* /lib/i386-linux-gnu/libz*
```

Your attempt to fix it may actually have done more harm than good. You attempted to install apt 1.0.1, which is for Ubuntu 14.04. On Ubuntu 16.04 you need apt [s]1.2.15[/s] 1.2.* (originally 1.2.15, updated version 1.2.24), which explains the dependency problems. So reinstall apt too, this time the right version.

---

### Post by eugenio.myles on 2017-10-11
I appreciate the help.
The directory you are looking for isn't there. Here is the full output none-the-less:
```

ls: cannot access '/lib/i386-linux-gnu/libz*': No such file or directory
lrwxrwxrwx. 1 root root     13 Mar  3  2017 /lib/x86_64-linux-gnu/libz.so.1 -> libz.so.1.2.8
-rw-r--r--. 1 root root 104864 Mar  3  2017 /lib/x86_64-linux-gnu/libz.so.1.2.8

```

I have a 64 bit Ubuntu, if I'm correct:
```

$ uname -a
Linux localhost 3.18.0-14875-g438cb8ab27c6 #1 SMP PREEMPT Sat Sep 16 09:58:36 PDT 2017 x86_64 x86_64 x86_64 GNU/Linux

```

Also, if it matters, I've installed this on a Acer Chromebook using Crouton.

---

### Post by ian-weisser on 2017-10-11
What were you trying to install or remove or otherwise accomplish *before* this problem started?

---

### Post by Impavidus on 2017-10-12
You have a 64 bit system and only have the 64 bit version of zlib, which is fine. It's correctly installed.

dpkg warned you were downgrading the 32 bit version of apt, although the .deb is labelled amd64. There are dependency problems with 2 different versions of libapt-pkg5.0, one 32 bit (original version for 16.04), the other 64 bit (updated version), breaking your old version (1.0.1) of apt. There's a missing dependency too, libapt-pkg4.12, but I guess that's because it's no longer required by apt 1.2.*.

It may be interesting to know how you got into this problem.

I think you'll have to use dpkg to install the recent versions of 64 bit apt and libapt-pkg5.0. I don't know why you would need 32 bit versions, but I don't know much about chromebooks and crouton, which may cause complications.

---

