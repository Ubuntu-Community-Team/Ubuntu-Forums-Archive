---
title: "still experiencing sudo apt-get update errors"
date: 2016-12-15
forum: General Help
---

### Post by crouchy89 on 2016-12-15
Hi All,
I know that this is a long-standing issue, but I have not been able to resolve the error messages when running ```
sudo apt-get update
```

The output I get is:

```

Get:1 http://ubuntu.mirrors.tds.net/pub/ubuntu xenial InRelease [247 kB]
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:3 http://dl.google.com/linux/chrome/deb stable Release
Get:4 http://dl.google.com/linux/chrome/deb stable Release.gpg [916 B]
Ign:4 http://dl.google.com/linux/chrome/deb stable Release.gpg   
Get:5 http://ubuntu.mirrors.tds.net/pub/ubuntu xenial-updates InRelease [102 kB]
Ign:1 http://ubuntu.mirrors.tds.net/pub/ubuntu xenial InRelease
Get:6 http://ubuntu.mirrors.tds.net/pub/ubuntu xenial-security InRelease [102 kB]
Ign:5 http://ubuntu.mirrors.tds.net/pub/ubuntu xenial-updates InRelease
Ign:6 http://ubuntu.mirrors.tds.net/pub/ubuntu xenial-security InRelease
Fetched 452 kB in 0s (518 kB/s)
Reading package lists... Done
W: GPG error: http://dl.google.com/linux/chrome/deb stable Release: At least one invalid signature was encountered.
W: The repository 'http://dl.google.com/linux/chrome/deb stable Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://ubuntu.mirrors.tds.net/pub/ubuntu xenial InRelease: At least one invalid signature was encountered.
W: The repository 'http://ubuntu.mirrors.tds.net/pub/ubuntu xenial InRelease' is not signed.N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://ubuntu.mirrors.tds.net/pub/ubuntu xenial-updates InRelease: At least one invalid signature was encountered.
W: The repository 'http://ubuntu.mirrors.tds.net/pub/ubuntu xenial-updates InRelease' is not signed.N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://ubuntu.mirrors.tds.net/pub/ubuntu xenial-security InRelease: At least one invalid signature was encountered.
W: The repository 'http://ubuntu.mirrors.tds.net/pub/ubuntu xenial-security InRelease' is not signed.N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

I have tried running:
```

[COLOR=#242729][FONT=Consolas]sudo apt-get clean
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]sudo mv /var/lib/apt/lists /tmp
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]sudo mkdir -p /var/lib/apt/lists/partial
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]sudo apt-get clean [/FONT][/COLOR][COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]sudo apt-get update[/FONT][/COLOR]
```

I tried updating my sources.list file, which now looks like the following:

```

cat /etc/apt/sources.list
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial universe multiverse
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial universe multiverse


deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial-updates universe
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial-updates universe


deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial-updates multiverse
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial-updates multiverse


deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial-security universe
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial-security universe
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial-security multiverse
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ xenial-security multiverse

```

I tried removing files from the following directory:

```

 ls /etc/apt/trusted.gpg.d
jockey-drivers.gpg   mc3man-gstffmpeg-keep.gpg   otto-kesselgulasch-gimp.gpg   steam.gpg~            webupd8team-java.gpg~
jockey-drivers.gpg~  mc3man-gstffmpeg-keep.gpg~  otto-kesselgulasch-gimp.gpg~  webupd8team-java.gpg

```

When that didn't work I put the files back as they were. The authentication tab in the Software & Updates looks like this:
[ATTACH=CONFIG]272721[/ATTACH]

Every solution I have come across has involved changing one of the options that I have listed, and continued searching has not yielded anything informative. Any help is greatly appreciated

Nick

---

### Post by #&amp;thj^% on 2016-12-15
Just went through this a couple of days ago... have a look: [https://ubuntuforums.org/showthread.php?t=2346051](https://ubuntuforums.org/showthread.php?t=2346051)

---

### Post by crouchy89 on 2016-12-15
A very in depth thread!

I followed it all the way though, it seems as though its just Chrome now that is causing a problem? The following code is from the end of that thread

```

/etc/apt/save$ sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4




$ cd /etc/apt
$ sudo mv sources.list.distUpgrade save/
$ sudo apt clean
$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                                     
Hit:3 http://archive.ubuntu.com/ubuntu xenial-security InRelease                                    
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                       
Get:5 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]
Get:6 http://dl.google.com/linux/chrome/deb stable Release.gpg [916 B]
Ign:6 http://dl.google.com/linux/chrome/deb stable Release.gpg
Reading package lists... Done   
W: GPG error: http://dl.google.com/linux/chrome/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991  NO_PUBKEY 1397BC53640DB551
E: The repository 'http://dl.google.com/linux/chrome/deb stable Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.




```

---

### Post by crouchy89 on 2016-12-15
To test this I tried installing updates through the Software Updating and unselecting Chrome. This worked, but the box for Ubuntu Base updates I could not select, so something still isnt right

---

### Post by mc4man on 2016-12-15
run
```
sudo apt-key list
```
Do you see 2 entries for Google?

---

### Post by crouchy89 on 2016-12-15
I dont seem to see any:

```

$ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12


pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>


pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>


pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

```

---

### Post by #&amp;thj^% on 2016-12-16
> **crouchy89 said:**
> A very in depth thread!

I followed it all the way though, it seems as though its just Chrome now that is causing a problem? The following code is from the end of that thread

```

/etc/apt/save$ sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4




$ cd /etc/apt
$ sudo mv sources.list.distUpgrade save/
$ sudo apt clean
$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                                     
Hit:3 http://archive.ubuntu.com/ubuntu xenial-security InRelease                                    
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                       
Get:5 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]
Get:6 http://dl.google.com/linux/chrome/deb stable Release.gpg [916 B]
Ign:6 http://dl.google.com/linux/chrome/deb stable Release.gpg
Reading package lists... Done   
W: GPG error: http://dl.google.com/linux/chrome/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991  NO_PUBKEY 1397BC53640DB551
E: The repository 'http://dl.google.com/linux/chrome/deb stable Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.




```

Just add the Google  key then:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 1397BC53640DB551
```
Here is my key list
```
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

[COLOR=#ff0000]pub   4096R/D38B4796 2016-04-12
uid                  Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
sub   4096R/640DB551 2016-04-12 [expires: 2019-04-12][/COLOR]

pub   4096R/F684460C 2016-02-14
uid                  Launchpad PPA for Reiner Herrmann

pub   4096R/1118213C 2015-08-12
uid                  Launchpad PPA for Graphics Drivers Team

pub   1024D/C1289A29 2009-11-11
uid                  Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>
sub   4096g/3FD59517 2009-11-11

pub   2048R/886DDD89 2009-09-04 [expires: 2020-08-29]
uid                  deb.torproject.org archive signing key
sub   2048R/219EC810 2009-09-04 [expires: 2018-08-30]

pub   1024R/EB2CC88B 2011-05-28
uid                  Launchpad PPA for I2P Maintainers

pub   4096R/54B8C8AC 2014-08-14
uid                  Launchpad PPA for MKUSB

pub   1024R/F59EAE4D 2012-04-01
uid                  Launchpad PPA for NoobsLab

pub   1024R/E2D0EBE9 2012-01-04
uid                  Launchpad PPA for RAVEfinity Project

pub   1024R/EEA14886 2010-05-04
uid                  Launchpad VLC

pub   1024R/02E04F78 2010-05-30
uid                  Launchpad xbmc


```

---

### Post by crouchy89 on 2016-12-16
Great! I didn't realize that updating the Google key would also sort the other issues. 

sudo apt-get update now runs without throwing any errors.

Thank you very much for your help both here and in the previous thread

---

### Post by #&amp;thj^% on 2016-12-16
Your Very Welcome.
Thanks for the Kind Words.

---

