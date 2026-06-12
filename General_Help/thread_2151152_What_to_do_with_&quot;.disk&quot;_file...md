---
title: "What to do with &quot;.disk&quot; file..?"
date: 2013-06-03
forum: General Help
---

### Post by KingNeil on 2013-06-03
I went to

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

And downloaded the Ubuntu 12.04 Windows WUBI installer.

The file is..

ubuntu-12.04.2-wubi-amd64.tar.xz

When I open the file in the Ubuntu archive manager, there are 2 files....

1. root.disk
2. wubildr

I would like to know... what am I supposed to do with these files...?

I am just trying to get an EXE, or installer file, that I can use to install Ubuntu from Windows...

---

### Post by oldos2er on 2013-06-03
The *.exe is here: [http://releases.ubuntu.com/precise/wubi.exe](http://releases.ubuntu.com/precise/wubi.exe)

---

### Post by KingNeil on 2013-06-03
> **oldos2er said:**
> The *.exe is here: [http://releases.ubuntu.com/precise/wubi.exe](http://releases.ubuntu.com/precise/wubi.exe)

Yeah, but the issue is... that's the EXE which requires you to download another piece of software

The reason I want the core installer is because I need to check the MD5 sum... I need some way to check the MD5 sum of the main WUBI file... the large one.

---

### Post by Cheesemill on 2013-06-04
Just use the wubi.exe file along with a downloaded iso file. If Wubi finds a Ubuntu iso file in the same location it's being run from it will use that instead of downloading the file itself.

Using this method you can check the MD5SUM of the downloaded Ubuntu iso before using it with wubi.

---

### Post by bcbc on 2013-06-04
Wubi doesn't check the MD5SUM of the disk image that you downloaded, but you can do this yourself with what's in [http://releases.ubuntu.com/12.04/MD5SUMS](http://releases.ubuntu.com/12.04/MD5SUMS)
Then to install using the diskimage see here: [http://askubuntu.com/a/143478/14916](http://askubuntu.com/a/143478/14916)

Wubi checks the MD5SUM of the ISO automatically, but Wubi.exe for 12.04.2 cannot install using the 64bit ISO due to a [bug]("https://bugs.launchpad.net/wubi/+bug/1134770"), but if you use this Wubi ([http://people.canonical.com/~evand/wubi/precise/wubi-r273-signed.exe](http://people.canonical.com/~evand/wubi/precise/wubi-r273-signed.exe)) it can install from the 64-bit ISO and check the MD5SUM at the same time.

---

