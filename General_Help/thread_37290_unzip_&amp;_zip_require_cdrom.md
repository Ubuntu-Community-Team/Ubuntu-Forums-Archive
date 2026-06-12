---
title: "unzip &amp; zip require cdrom?"
date: 2005-05-26
forum: General Help
---

### Post by vehyla on 2005-05-26
Today I tried to apt-get zip & unzip and for both of them I get a message requiring cdrom.  Is this normal?  If so then how do I get these applications as I tried the cd I used to boot up and download Ubuntu and that did not seem to work.

Here is what it looks like:
echelon:~> sudo apt-get install unzip                                         [16:33]
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  zip
The following NEW packages will be installed:
  unzip
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/134kB of archives.
After unpacking 315kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

echelon:~> sudo apt-get install zip                                           [16:33]
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  unzip
The following NEW packages will be installed:
  zip
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/92.4kB of archives.
After unpacking 238kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

---

### Post by SFN on 2005-05-26
You still have the CD line in your apt sources.

Do this:

```
sudo gedit /etc/apt/sources.list
``` 

The top line should be the line pointing to your CD-ROM. Put a # at the beginning of that line, save and exit.

Then do:

```
sudo apt-get update
``` 

Once the update is completed, try to install unzip again.

---

### Post by vehyla on 2005-05-27
That worked.  Thank you.

---

