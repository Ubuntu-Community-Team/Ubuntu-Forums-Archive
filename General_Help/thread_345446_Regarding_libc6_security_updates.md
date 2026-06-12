---
title: "Regarding libc6 security updates"
date: 2007-01-24
forum: General Help
---

### Post by jdong on 2007-01-24
**UPDATE: A new version of this update has been released and will install correctly for all users. This notice is kept here for historical purpose, and will be unstickied in 24 hours.  The updated version of the libc6 packages is "2.4-1ubuntu12.3".**

Some users attempting to apply the recent libc6 (glibc) security updates may get an error that looks something like this:

```

(Reading database ... 160320 files and directories currently installed.)
Preparing to replace libc6-dev 2.4-1ubuntu12 (using .../libc6-dev_2.4-1ubuntu12.2_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.4-1ubuntu12.2_i386.deb) ...
Matching libraries: **(list of library files)**

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.4-1ubuntu12.2); however:
  Version of libc6 on system is 2.4-1ubuntu12.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev

```

This appears to affect a minor portion of people and is caused by the presence of offending library files. This includes libpthread20 (from the repositories, but typically not installed) and some other reported files that cannot be traced to Ubuntu repositories in origin (binary NVidia beta drivers are suspected, but not confirmed). Developers are puzzled at what could be installing the libpthread20 package or making the erroneous links, and are asking for users' help in pinpointing the culprits. Nonetheless, a fixed package is in the works and will be released soon.


**If You Are Affected**:

A fix to this is issue is in the works. Just sit tight and wait for a newer update which will correct this situation. **Please do not attempt any recovery instructions that tell you to temporarily move or delete library files** to coerce the update to install. That is a highly risky procedure and could break your system beyond all but expert repair.

**So is it safe to apply libc6 updates?**

The offending packages have been blocked at the download servers so as of now, it should not be possible to download (and thus install) this update. So for now, it is fairly safe to attempt to apply any updates the Update Manager finds for you. An attempt to download the broken package will fail with a message like this:
```

W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb
   403 Forbidden [IP: 195.248.90.35 80]

```



**I have been affected. Is there any way I can help provide debugging information?**
Yes. Some developers have asked for assistance from users who experience this problem:

[quote=Keybuk]
We are trying to understand why people have libpthread20 installed, as it's not used by anything in the Ubuntu archive...

Could people supply the output of:

zgrep pthread /var/log/dpkg.log*
[/quote]

If you are able to supply the output of the listed command, post as a reply to this thread.

References:

Launchpad bug: [https://launchpad.net/ubuntu/+source/glibc/+bug/81125](https://launchpad.net/ubuntu/+source/glibc/+bug/81125)
Keybuk's post: [http://ubuntuforums.org/showthread.php?p=2057688&highlight=cjwatson#post2057688](http://ubuntuforums.org/showthread.php?p=2057688&highlight=cjwatson#post2057688)
Matt D Zimmerman urging people not to try workarounds: [http://ubuntuforums.org/showpost.php?p=2057387&postcount=29](http://ubuntuforums.org/showpost.php?p=2057387&postcount=29)
cjwatson (Colin Watson) advising the same: [http://ubuntuforums.org/showpost.php?p=2057057&postcount=23](http://ubuntuforums.org/showpost.php?p=2057057&postcount=23)

---

### Post by muzzol on 2007-01-24
here it is:

```
[lila:~]# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy
[lila:~]# zgrep pthread /var/log/dpkg.log*
/var/log/dpkg.log.2.gz:2006-11-07 12:02:11 install libpthread20 <cap> 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:11 status half-installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:11 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:11 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:12 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:12 status half-configured libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:16 status installed libpthread20 2.0.7-2ubuntu2

```

this laptop doesnt have a nvidia card.

any other command that can help?

---

### Post by cjwatson on 2007-01-24
Could we have the whole /var/log/dpkg.log, please? It would be useful to see context around that installation, to try to guess at why libpthread20 got installed.

---

### Post by jdong on 2007-01-24
> **muzzol said:**
> here it is:

```
[lila:~]# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy
[lila:~]# zgrep pthread /var/log/dpkg.log*
/var/log/dpkg.log.2.gz:2006-11-07 12:02:11 install libpthread20 <cap> 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:11 status half-installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:11 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:11 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:12 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:12 status half-configured libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-07 12:02:16 status installed libpthread20 2.0.7-2ubuntu2

```

this laptop doesnt have a nvidia card.

any other command that can help?

Can you attach the entire dpkg.log.2.gz to t he linked Launchpad bug report, stating that it shows libpthread20 being installed for some reason?

---

### Post by Pajblito on 2007-01-24
same problem here, cant update those libraries :(

```
##
## Started installation of xfce4 at 11:43h
##
## Visit http://forum.xfce.org/ if you have problems using this installer.
##

# Environment variables
PATH is set to "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/bin:/usr/bin:/usr/local/ssl/bin:/usr/local/bin:/opt/openssl/bin:/usr/local/openssl/bin:/usr/pkg/bin:/usr/ucb:/usr/X11R6/bin:/usr/X11R6/bin:/usr/openwin/bin:/usr/local/bin:/opt/local/bin:/usr/pkg/bin:/opt/gnome2/bin:/opt/gnome/bin:/opt/xfce4/bin:/opt/xfce/bin:/home/pablito/local/bin:/home/pablito/xfce/bin:/home/pablito/xfce4/bin"
PKG_CONFIG_PATH is set to ":/usr/lib/pkgconfig:/usr/lib/pkgconfig"

## Checking for usable C compiler
gcc --version
./bootstrap.sh: 46: gcc: not found
## Checking for usable C++ compiler
g++ --version
./bootstrap.sh: 67: g++: not found
## Checking for GNU make
gmake --version
make --version
gnumake --version
GNUmake --version
./bootstrap.sh: 92: GNUmake: not found

## Checking for package config tool
pkg-config --version
0.20

## Checking for GLib (GModule) >= 2.6.0
pkg-config --atleast-version=2.6.0 glib-2.0 gmodule-2.0
!! Please install GLib 2.6.0 or above and the GLib development files. It is
!! important that you install GModule, which is part of GLib as well. GLib
!! can be downloaded from http://www.gtk.org/.

```

```

W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.2_i386.deb
  403 Forbidden [IP: 195.248.90.35 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.4-1ubuntu12.2_i386.deb
  403 Forbidden [IP: 195.248.90.35 80]

```

---

### Post by F0EHammer_dg on 2007-01-24
```

>:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy

>:~$ zgrep pthread /var/log/dpkg.log*
/var/log/dpkg.log:2007-01-03 13:34:55 install libpthread20 <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:34:55 status half-installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:34:55 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:34:55 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:34:55 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:34:55 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:34:55 status not-installed libpthread-dev <none>
/var/log/dpkg.log:2007-01-03 13:34:56 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:34:56 status half-configured libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:34:58 status installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:35:34 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:35:34 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:35:34 status not-installed libpthread-dev <none>
/var/log/dpkg.log:2007-01-03 13:36:55 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:36:55 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:36:55 status not-installed libpthread-dev <none>
/var/log/dpkg.log:2007-01-03 13:38:35 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:38:35 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:38:35 status not-installed libpthread-dev <none>
/var/log/dpkg.log:2007-01-03 13:38:55 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:38:55 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-03 13:38:55 status not-installed libpthread-dev <none>

```

---

### Post by iteranq on 2007-01-24
Here is the output:

/var/log/dpkg.log.3.gz:2006-10-27 09:20:33 install libpthread20 <none> 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-27 09:20:33 status half-installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-27 09:20:33 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-27 09:20:33 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-27 09:20:33 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-27 09:20:33 status half-configured libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-27 09:20:33 status installed libpthread20 2.0.7-2ubuntu2

This laptop does not have a nvidia card, it has a intel 915 gm

Regards,
Ivan Teran

---

### Post by pardalek on 2007-01-24
Here are mine:
```

xxx@yyy:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy


xxx@yyy:~$ zgrep pthread /var/log/dpkg.log*
/var/log/dpkg.log.3.gz:2006-10-25 19:56:28 install libpthread20 <žádná> 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-25 19:56:28 status half-installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-25 19:56:28 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-25 19:56:28 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-25 19:56:29 install libpthread-dev <žádná> 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-25 19:56:29 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-25 19:56:29 status not-installed libpthread-dev <žádná>
/var/log/dpkg.log.3.gz:2006-10-25 19:56:30 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-25 19:56:30 status half-configured libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.3.gz:2006-10-25 19:56:41 status installed libpthread20 2.0.7-2ubuntu2
```

---

### Post by pardalek on 2007-01-24
Also, since the "update" I can't start my X11 with the latest nvidia driver (9746) which I compiled manually. Now I can't build it again and even "apt-get -f install" doesn't work ;(. Can't install anything ;(. This is the error output when I use nvidia driver:
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux scarpia 2.6.19.1rocking1 #2 Sun Jan 7 08:56:16 CET 2007 i686
Build Date: 07 July 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 24 23:52:24 2007
(==) Using config file: "/etc/X11/xorg.conf"

error opening security policy file /usr/lib/xserver/SecurityPolicy

Backtrace:
0: /usr/bin/X.schedreal(xf86SigHandler+0x81) [0x80c3971]
1: [0xb7fbd420]
2: /usr/bin/X.schedreal(xf86NameCmp+0x24) [0x80c7174]
3: /usr/bin/X.schedreal(InitInput+0xf2) [0x809f1a2]
4: /usr/bin/X.schedreal(main+0x355) [0x806e5e5]
5: /lib/libc.so.6(__libc_start_main+0xdc) [0xb7dcd8cc]
6: /usr/bin/X.schedreal(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
```

---

### Post by jdong on 2007-01-24
> **pardalek said:**
> Also, since the "update" I can't start my X11 with the latest nvidia driver (9746) which I compiled manually. Now I can't build it again and even "apt-get -f install" doesn't work ;(. Can't install anything ;(. This is the error output when I use nvidia driver:

Hmm, this does not appear related to this particular libc6 issue, and does not happen with any official Ubuntu nvidia drivers.... so please make a separate thread discussing this issue.

---

### Post by Shelnutt2 on 2007-01-24
I think I have an issue with libc6 also. I did an update two days ago, and then I restart into windows (I don't have my canon IP4200 working yet). When I went to boot into Linux then the xserver stopped working. I get a blank/black screen and thats all I get. I had a thread [here]("http://www.ocforums.com/showthread.php?p=4901994") but we didn't come up with a solution and then now this issue. I tried the [solution ]("http://ubuntuforums.org/showthread.php?t=344980")of purging then reinstalling libpthread20, but turns out I don't have libpthread20 installed. I then decided to install libpthread20 just because linux/any os is weird and I'm willing to try anything to get it working again. Well it didn't work so I the purged libpthread20 from my system.

libc6 installed fine for me, no error messages. Still want my dpkg.log file?

Oh and I'm running the frglx drivers for my ATI X1650.

---

### Post by madscientist on 2007-01-24
To fix the nvidia problem I think you need to reconfigure the nvidia packages.  After I successfully updated to the new libc6 (if you do a "check" it will update your package list, then you can update) I did this:

sudo dpkg-reconfigure nvidia-kernel-common
sudo dpkg-reconfigure nvidia-glx

then I was able to start with the "nvidia" driver instead of the NV driver (from the console (CTRL-ALT-F1) log in, then run "sudo /etc/init.d/gdm stop" then "sudo /etc/init.d/gdm start")

You have to do this every time you install a new kernel and reboot.

---

### Post by madscientist on 2007-01-24
As for the libc6 problem, I reported the original bug in Launchpad.  I haven't been able to figure out where those symlinks came from.  I have the nvidia stuff installed but that doesn't seem to be the culprit.  I also tried the zgrep command provided in the original message and nothing matched (nothing was printed).

And, I don't have libpthread20 installed.

I also looked through my entire system for any other files that had been modified within an hour of when those symlinks /usr/lib/libc.so.6 and /usr/lib/libm.so.6 were created, and there was nothing of interest there.

So, I have no idea where those came from.

I've deleted those extra symlinks and I'm waiting to see what, if anything, stops working on my system :-| .

---

### Post by orb9220 on 2007-01-24
Was unable just now to update
libc6
libc6-dev
libc6-1686

Get a 

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb)
  403 Forbidden [IP: 195.248.90.35 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.2_i386.deb)
  403 Forbidden [IP: 195.248.90.35 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.4-1ubuntu12.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.4-1ubuntu12.2_i386.deb)
  403 Forbidden [IP: 195.248.90.35 80]

Something I am doing wrong?
Thanks

---

### Post by Shelnutt2 on 2007-01-24
> **orb9220 said:**
> Was unable just now to update
libc6
libc6-dev
libc6-1686

Get a 



Something I am doing wrong?
Thanks

No, your doing it right. But the first post states that they have locked the libc6 files, in order to stop the spread of this weird error/trouble people are getting.

---

### Post by shendric on 2007-01-24
> **jdong said:**
> **UPDATE: A new version of this update has been released and will install correctly for all users. This notice is kept here for historical purpose, and will be unstickied in 24 hours.  The updated version of the libc6 packages is "2.4-1ubuntu12.3".**


The version I see in the Update Manager is 2.3.6-0ubuntu20.2, not 2.4-1ubuntu12.3.  I've tried refreshing, but that's the only version I get.  Should I be seeing 2.4-1ubuntu12.3 on 6.06?

---

### Post by orb9220 on 2007-01-24
> UPDATE: A new version of this update has been released and will install correctly for all users. This notice is kept here for historical purpose, and will be unstickied in 24 hours. The updated version of the libc6 packages is "2.4-1ubuntu12.3".

Saw that and thought it had been fixed? Read further and now I throw myself onto the "Fires of the Goddess Ubuntu" in repentance

---

### Post by jdong on 2007-01-24
> **orb9220 said:**
> Was unable just now to update
libc6
libc6-dev
libc6-1686

Get a 



Something I am doing wrong?
Thanks

It's still trying to pull the older version. Update your package list (open up Synaptic and hit the reload button; or click the Check For Updates button on the update manager) and try again.

The update may not have hit all the mirrors yet, so further patience may be necessary.

---

### Post by madscientist on 2007-01-25
Right, you have to refresh your package list.  And you might be using a mirror.  FYI, I was able to get and install the updated libraries as of about 5pm (EST, or GMT-5) on Wednesday (24 Jan).
They are there; if it doesn't work for you wait a bit and try again.

---

### Post by cjwatson on 2007-01-25
No; this problem and this thread only affected 6.10, not 6.06 (although we may be issuing an similar fix for 6.06 as well as a preventative measure; it's much less urgent).

---

### Post by frisket on 2007-01-25
> **jdong said:**
> 
Yes. Some developers have asked for assistance from users who experience this problem:
If you are able to supply the output of the listed command, post as a reply to this thread.


  # zgrep pthread /var/log/dpkg.log*
  #

It produces nothing on this Dell Inspiron 4150 running Edgy. The original error was

  W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb)
  404 Not Found [IP: 193.1.193.69 80]
  W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.2_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.2_i386.deb)
  404 Not Found [IP: 193.1.193.69 80]
  W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.4-1ubuntu12.2_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.4-1ubuntu12.2_i386.deb)
  404 Not Found [IP: 193.1.193.69 80]

  # ls -l /var/log/dpkg*
  -rw-r----- 1 root adm 28963 2007-01-24 22:47 /var/log/dpkg.log
  -rw-r----- 1 root adm 78144 2006-12-23 11:46 /var/log/dpkg.log.1
  -rw-r----- 1 root adm 62149 2006-11-28 12:41 /var/log/dpkg.log.2.gz
  #

I've attached those files.

---

### Post by jdong on 2007-01-25
No, that's not the error we're after. The first snippet from my original post is the type of error we want. Your error simply states that your update manager was trying to download the broken update, and was stopped from doing so.

---

### Post by a-musing amazon on 2007-01-25
> **cjwatson said:**
> No; this problem and this thread only affected 6.10, not 6.06 (although we may be issuing an similar fix for 6.06 as well as a preventative measure; it's much less urgent).

This seems to be incorrect, as regards 6.06 (I run the 64-bit version). I tried updating in Dapper and ended up with broken Packages. Its still wanting to update to 2.3.6-0ubuntu20.2 from 2.3.6-0ubuntu20.

I'm not running the NVidea drivers - I use the ATI ones, however I do have various libpthread libraries installed.

---

### Post by GringoCroco on 2007-01-26
/var/log/dpkg.log:2007-01-21 14:53:31 install libpthread20 <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:53:31 status half-installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:53:31 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:53:31 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:53:31 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:53:31 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:53:32 status not-installed libpthread-dev <none>
/var/log/dpkg.log:2007-01-21 14:53:32 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:53:32 status half-configured libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:53:38 status installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:54:24 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:54:24 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:54:24 status not-installed libpthread-dev <none>
/var/log/dpkg.log:2007-01-21 14:58:29 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:58:29 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:58:29 status not-installed libpthread-dev <none>
/var/log/dpkg.log:2007-01-21 14:59:30 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:59:30 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:59:30 status unpacked libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:59:30 status unpacked libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:59:31 status unpacked libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:59:31 status half-configured libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 14:59:31 status installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 remove libpthread-dev 2.0.7-2ubuntu2 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status half-configured libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status config-files libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status config-files libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status config-files libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status not-installed libpthread-dev <none>
/var/log/dpkg.log:2007-01-21 15:03:44 status installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 remove libpthread20 2.0.7-2ubuntu2 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status half-configured libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status half-installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status config-files libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 purge libpthread20 2.0.7-2ubuntu2 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status config-files libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status config-files libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status config-files libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status config-files libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status config-files libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log:2007-01-21 15:03:44 status not-installed libpthread20 <none>


I do have nvidia drivers.
I tryed to install libpthread-dev because I needed to work on some projects, but an error ocured (confilt with glibc (it complained about an already existent /usr/include/pthread.h which was put there by glibc))

i've attached dpkg.log and dpkg.log.1 if they are of any interest to you

---

### Post by jdong on 2007-01-26
pthread development libraries are already provided by glibc and, if needed, libpth-dev... But yeah, I can kinda understand what would lead to that :)

---

### Post by sorgud on 2007-01-26
Hi,
I have done an apt-get update && apt-get upgrade and the libc6, libc6-dev and libc6-i686 were upgrade. 
I have installed, then, all the three: 2.4-1ubuntu12.3 . It should be OK, but...
The charmap is absolutelly crazy. In a "konsole" I have the following message:
Current locale charmap `ANSI_X3.4-1968'
My locale read:
locale
LANG=en_US.UTF-8
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=C
I don't know where to look for the error....
thanks in advance
talueguito
raul

---

### Post by hikaricore on 2007-01-26
I'm not affected by this issue however I downgraded my packages to libc6 2.4-1ubuntu12.2 due to a systemwide slowdown after this update.

I made a thread about this issue yesterday: [http://ubuntuforums.org/showthread.php?t=346529](http://ubuntuforums.org/showthread.php?t=346529)

---

### Post by frisket on 2007-01-28
> **jdong said:**
> No, that's not the error we're after. The first snippet from my original post is the type of error we want. Your error simply states that your update manager was trying to download the broken update, and was stopped from doing so.

Ah. OK, sorry. That was abundantly unclear from the original post. The new version has evidently fixed the problem anyway...many thanks to all concerned.

---

