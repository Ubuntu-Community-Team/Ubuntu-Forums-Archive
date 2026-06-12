---
title: "libreoffice won't start"
date: 2018-02-25
forum: General Help
---

### Post by georgeskesseler on 2018-02-25
Classic error message:
> LibreOffice user installation could not be processed due to missing  access rights. Please make sure that you have sufficient access rights  for the following location and restart LibreOffice
/data/home/georges/.config/libreoffice/4


Not much information in there what to look out for.

I deleted the complete ~/.config/libreoiffice before doing this post. It did not help.

So here is my debug:
```
$ ls -ld ~/.config/ ~/.config/libreoffice/ ~/.config/libreoffice/4
drwx------ 72 georges users   4096 Feb 25 15:54 /home/georges/.config/
drwxrwxr-x  3 georges georges 4096 Feb 25 15:54 /home/georges/.config/libreoffice/
drwxrwxr-x  3 georges georges 4096 Feb 25 15:54 /home/georges/.config/libreoffice/4
```

And a trace...
```
[...]
lstat("/data/home/georges", {st_mode=S_IFDIR|0755, st_size=94208, ...}) = 0
lstat("/data/home/georges/.config", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
lstat("/data/home/georges/.config/libreoffice", {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
lstat("/data/home/georges/.config/libreoffice/4", {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
access("/tmp", W_OK)                    = 0
stat("/proc/version", {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
access("/home/georges/.Xauthority", R_OK) = 0
openat(AT_FDCWD, "/home/georges/.Xauthority", O_RDONLY) = -1 EACCES (Permission denied)
openat(AT_FDCWD, "/usr/lib/libreoffice/program/intro-en_US.png", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/X11/locale/locale.alias", O_RDONLY) = 4
openat(AT_FDCWD, "/usr/share/X11/locale/locale.dir", O_RDONLY) = 4
access("/usr/share/X11/locale/C/XLC_LOCALE", R_OK) = 0
[...]
```


Huh? Xauthority EACCESS?
first why does it need that, second, why is access not ok?
```
$ ls -ld ~/.Xauthority 
-rw------- 1 georges georges 254 Jan  6 18:42 /home/georges/.Xauthority

```

Another EACESS is this one
```
[...]
lstat("/etc", {st_mode=S_IFDIR|0755, st_size=12288, ...}) = 0
lstat("/etc/libreoffice", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat("/etc/libreoffice/sofficerc", {st_mode=S_IFREG|0644, st_size=419, ...}) = 0
openat(AT_FDCWD, "/etc/libreoffice/sofficerc", O_RDONLY) = 4
openat(AT_FDCWD, "/etc/libreoffice/sofficerc", O_RDONLY) = 4
stat("/usr/lib/libreoffice/program/", {st_mode=S_IFDIR|0755, st_size=20480, ...}) = 0
openat(AT_FDCWD, "/sys/dev/block/253:0/queue/rotational", O_RDONLY) = -1 EACCES (Permission denied)
openat(AT_FDCWD, "/usr/lib/libreoffice/program/pagein-common", O_RDONLY) = 4
openat(AT_FDCWD, "/usr/lib/libreoffice/program/libmergedlo.so", O_RDONLY) = 5
openat(AT_FDCWD, "/usr/lib/libreoffice/program/libi18nlangtag.so", O_RDONLY) = 5
[...]
```



```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

$ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libreoffice is already the newest version (1:5.4.5-0ubuntu0.17.10.1).
0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.
```

---

### Post by Don_Murray on 2018-02-25
I'm seeing these exact same symptoms.

---

### Post by wildmanne39 on 2018-02-25
Hello and welcome to the forums, please start your own thread instead of posting in someone else's so you can get the help you need and so can the person that started this one.

Thanks

---

### Post by iken2 on 2018-02-25
I have experienced the same issue with the same version of Ubuntu and LibreOffice.

However, some additional detail.

My home directory root is /house instead of /home.  /house lives on a different mount point and on an ext4 partition.
All other attempted methods for accessing files works properly.
If the .config/libreoffice directory is purged, libreoffice recreates it and most of the expected content as expected.

If the user home directory is copied into /home and /etc/passwd changed to point to this home dir location, libreoffice works perfectly for editing documents located in that directory root.
Libreoffices gives an "access denied" message to attempts to open the same file under the /house root.  Both files are owned by the same user and group and have the same perms.
They were copied with cp -p

/house mount point is owned by root:root with perm 755.  There are no mount options currently.

If the user home directory is set to /house/username    libreoffice always fails to start with the error condition specified by georgekessler

I can work around this for my situation, so I am posting here in case it may pertain to georgekessler's issue as his home root is also other than default.

Best,
Mark

---

### Post by wildmanne39 on 2018-02-25
Hello and welcome to the forums, please start your own thread instead of posting in someone else's so you can get the help you need and so can the person that started this one.

Thanks

---

### Post by georgeskesseler on 2018-02-26
Intersting. My home also is on another partition
```
 georges:1001:1001:Georges,,,:/home/georges:/bin/bash
```

Protections are all ok

```
 $ ls -fld / /home /home/georges /data /data/home /data/home/georges
drwxr-xr-x  25 root    root   4096 Feb 22 06:51 /
drwxr-xr-x   3 root    root   4096 Sep 22 23:27 /home
lrwxrwxrwx   1 root    root     18 Sep 21 00:50 /home/georges -> /data/home/georges
drwxr-xr-x   4 root    root   4096 Dez 16  2014 /data
drwxr-xr-x  32 root    root   4096 Mär 27  2016 /data/home
drwxr-xr-x 242 georges users 94208 Feb 26 18:37 /data/home/georges

```

A bit of test:
```
 georges:1001:1001:Georges,,,:/data/home/georges:/bin/bash
```

The error did not go away (after relogin).
I have a second user on the system, same error.

---

### Post by georgeskesseler on 2018-02-26
Tested and confirmed the bug mentioned by[**[COLOR=#000000]iken2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2091446")

Create new user:
```
 useradd -m lotest
passwd lotest 
vi /etc/passwd    # change /home/lotest to /data/home/lotest
mv /home/lotest /data/home/
ln -s /data/home/lotest /home/
ls -l /home/
```

confirmed: libreoffcie does not work

```
 rm /home/lotest
mv /data/home/lotest /home/
vi /etc/passwd   # change /data/home/lotest to /home/lotest
```

confirmed: libreoffice works!

---

### Post by georgeskesseler on 2018-02-26
Found a bug from 2014
added my diagnostic to that

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1292407](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1292407)

created a new bug
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751854](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751854)

---

### Post by DuckHook on 2018-02-26
This is a problem with libreoffice's new apparmor profile. It popped up on my install after the latest update. Details here: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005)

Workaround is to disable libreoffice's apparmor profile for now, the command for which is given in post #10: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005/comments/10](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005/comments/10)

I have a number of non-standard locations that hold libreoffice docs. It isn't practical for me to haul everything into /home, and I don't want unnecessary symlinks all over the place either.

If you are familiar with apparmor, you can retrain your apparmor profile to include the nonstandard locations. Otherwise, the above workaround will do. I don't usually recommend disabling apparmor profiles, but it appears that this is what the devs are planning for the next upgrade, so it is going to be the default behaviour anyway.

---

### Post by georgeskesseler on 2018-02-26
Thanks, now libreoffice works.

One question remains, as I read in the bug, in the future more of apparmor related issues might come up. As I like to use my ubuntu as a dumb desktop user and not as a knowledgable linux nerd, is it possible to make apparmor related issues more visible towards the end-user?

For those who stumble on this forum post (the bug is somehow not popping up on google searches) here is what to do so you don't need to read through the whole bug post:

disable apparmor temporarily for libreoffice
```
 sudo apparmor_parser -R /etc/apparmor.d/usr.lib.libreoffice.program.*
```

disable apparmor permanently for libreoffice (not recommended)
```
 sudo ln -s /etc/apparmor.d/usr.lib.libreoffice.program.* /etc/apparmor.d/disable/
```

---

### Post by vasa1 on 2018-02-26
> **georgeskesseler said:**
> ...
One question remains, as I read in the bug, in the future more of apparmor related issues might come up. As I like to use my ubuntu as a dumb desktop user and not as a knowledgable linux nerd, is it possible to make apparmor related issues more visible towards the end-user?
...
Well, first-time users would presumably use defaults. In which case, apparmor settings are just fine. Knowledgeable users who move away from defaults will, I hope, ask for directions if they run into issues.

---

### Post by wildmanne39 on 2018-02-26
I have installed libreoffice 6 on two computers in the last couple of days and apparently this has been fixed so when it come out in 18.04 this will no longer be an issue or if users or running older versions of ubuntu they can upgrade to libreoffice 6 and no profiles have to be disabled.

---

### Post by DuckHook on 2018-02-26
> **georgeskesseler said:**
> …One question remains, as I read in the bug, in the future more of apparmor related issues might come up. As I like to use my ubuntu as a dumb desktop user and not as a knowledgable linux nerd, is it possible to make apparmor related issues more visible towards the end-user?…
Good question.

One of the reasons that Ubuntu is not a malware pit is due to apparmor. It fences in things like virtual machines, CUPS, LXD and other potentially exploitable apps so that rogue behaviour is jailed within a confined sandbox. Unfortunately, when it does its magic—a little too aggressively in this case—the system sometimes mistakes its actions for something unrelated. In the LibreOffice issue, the system reported a lack of permission to access the file, which most people would naturally assume to mean file permissions. It led me astray for a few minutes too, before a log search pointed to apparmor and then a Google search led to the Launchpad bug report.

I'm not sure how to make apparmor reports more descriptive. I agree that they should be. Not only for cases like this one where apparmor was confining too aggressively, but especially where it detects a real rogue process. It would be nice for apparmor to generate a popup saying something to the effect that: "Apparmor has denied an unauthorized access attempt by LibreOffice", or something like that. Then again, I'm not a developer and I don't understand how difficult this may be to implement.

What I try to keep in mind is that Ubuntu tries hard to cover all bases. I appreciate the OS even if it is sometimes rough around the edges. In this case, you may want to add your suggested Apparmor phrasing to the various Launchpad bug reports that already exist to deal with this ticket. I've found that courteous  and respectful suggestions are always welcomed by the devs.

---

### Post by georgeskesseler on 2018-02-26
As long as applications create dozens of errors in apparmor, it's unrealistic to show these via popup.
On the other hand, libreoffice even does not know that this privilege violation is caused by apparmor. Liberoffice just gets an EACCESS and can't do more than showing that to the end user, who is then puzzled of what's going on.

Here is one single libreoffice start... I would not like to get 10 popup windows :-)

```
Feb 26 18:48:28 breeze kernel: [4406851.350256] audit: type=1400 audit(1519667308.941:4576): apparmor="DENIED" operation="open" profile="libreoffice-oopslash" name="/data/home/lotest/.Xauthority" pid=28338 comm="oosplash" requested_mask="r" denied_mask="r" fsuid=1003 ouid=1003
Feb 26 18:48:28 breeze kernel: [4406851.365087] audit: type=1400 audit(1519667308.957:4577): apparmor="DENIED" operation="open" profile="libreoffice-oopslash" name="/sys/devices/virtual/block/dm-0/queue/rotational" pid=28338 comm="oosplash" requested_mask="r" denied_mask="r" fsuid=1003 ouid=0
Feb 26 18:48:29 breeze kernel: [4406851.596300] audit: type=1400 audit(1519667309.189:4578): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/data/home/lotest/.Xauthority" pid=28373 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1003 ouid=1003
Feb 26 18:48:29 breeze kernel: [4406851.596927] audit: type=1400 audit(1519667309.189:4579): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/data/home/lotest/.Xauthority" pid=28372 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1003 ouid=1003
Feb 26 18:48:29 breeze kernel: [4406851.597720] audit: type=1400 audit(1519667309.189:4580): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/uevent" pid=28373 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1003 ouid=0
Feb 26 18:48:29 breeze kernel: [4406851.597735] audit: type=1400 audit(1519667309.189:4581): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/uevent" pid=28373 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1003 ouid=0
Feb 26 18:48:29 breeze kernel: [4406851.603710] audit: type=1400 audit(1519667309.193:4582): apparmor="DENIED" operation="mkdir" profile="libreoffice-soffice" name="/data/home/lotest/.config/libreoffice/4/user/extensions/" pid=28372 comm="soffice.bin" requested_mask="c" denied_mask="c" fsuid=1003 ouid=1003
Feb 26 18:48:29 breeze kernel: [4406851.613277] audit: type=1400 audit(1519667309.205:4583): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/uevent" pid=28373 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1003 ouid=0
Feb 26 18:48:29 breeze kernel: [4406851.613293] audit: type=1400 audit(1519667309.205:4584): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/uevent" pid=28373 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1003 ouid=0
Feb 26 18:48:29 breeze kernel: [4406851.613314] audit: type=1400 audit(1519667309.205:4585): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/uevent" pid=28373 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1003 ouid=0

```

Solving this is quite a challenge I guess, but it should be adressed somehow.
Does "ubuntu-bug libreoffice" include syslog entries relative to the application being reported? 
This could even give direct feedback to the user "I found apparmor DENIED messages in /var/log/syslog, are use using libreoffice in a non standard setup?"

---

### Post by DuckHook on 2018-02-28
Just received the latest LibreOffice update in which its apparmor profile has been disabled:```
apt-listchanges: Changelogs
---------------------------
…

libreoffice (1:5.4.5-0ubuntu0.17.10.4) artful; urgency=medium

  * debian/libreoffice-common.preinst.in: added to disable apparmor profiles on
    fresh installs and upgrades from 1:5.4.5-0ubuntu0.17.10.1 (LP: #1751005)
  * debian/patches/apparmor-senddoc-fixes.patch: updated to reflect upstream
    commit

 -- Olivier Tilloy <olivier.tilloy@canonical.com>  Mon, 26 Feb 2018 15:17:18 +0100
…
```
We are back to training and implementing our own apparmor profiles, I guess.

---

### Post by vasa1 on 2018-02-28
Yep! See [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005/comments/24](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005/comments/24) and [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005/comments/31](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005/comments/31)

---

### Post by bilkay on 2018-04-22
> **georgeskesseler said:**
> Thanks, now libreoffice works.

One question remains, as I read in the bug, in the future more of apparmor related issues might come up. As I like to use my ubuntu as a dumb desktop user and not as a knowledgable linux nerd, is it possible to make apparmor related issues more visible towards the end-user?

For those who stumble on this forum post (the bug is somehow not popping up on google searches) here is what to do so you don't need to read through the whole bug post:

disable apparmor temporarily for libreoffice
```
 sudo apparmor_parser -R /etc/apparmor.d/usr.lib.libreoffice.program.*
```

disable apparmor permanently for libreoffice (not recommended)
```
 sudo ln -s /etc/apparmor.d/usr.lib.libreoffice.program.* /etc/apparmor.d/disable/
```

Server or client or both?

---

