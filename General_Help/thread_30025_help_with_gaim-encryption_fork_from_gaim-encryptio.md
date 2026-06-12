---
title: "help with gaim-encryption: fork from gaim-encryption backports request"
date: 2005-04-26
forum: General Help
---

### Post by ubuntu27 on 2005-04-26
I suppose you guys are talking about Gaim-Encryption from [http://gaim-encryption.sourceforge.net/](http://gaim-encryption.sourceforge.net/)

How do I install Gaim Encryotion !?? 

My OS is Ubuntu 5.04 [Hoary Wedgedhog]

I will apreciate step by step instructions.  :wink:

---

### Post by TravisNewman on 2005-04-26
sudo apt-get install gaim-encryption ;)

---

### Post by ubuntu27 on 2005-04-26
Thanks, I never though that it was part in the respositories...
One more question, how do I use it?   :roll:   :-? 

***********************

ubuntu27@ubuntu27:~$ sudo apt-get install gaim-encryption
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  gaim-encryption
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 83.8kB of archives.
After unpacking 451kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gaim-encryption 2.35-0ubuntu1 [83.8kB]
Fetched 83.8kB in 0s (109kB/s)

Preconfiguring packages ...
Selecting previously deselected package gaim-encryption.
(Reading database ... 65138 files and directories currently installed.)
Unpacking gaim-encryption (from .../gaim-encryption_2.35-0ubuntu1_i386.deb) ...
Setting up gaim-encryption (2.35-0ubuntu1) ...
ubuntu27@ubuntu27:~$

---

### Post by Technoviking on 2005-04-26
[QUOTE=ubuntu27]Thanks, I never though that it was part in the respositories...
One more question, how do I use it?   :roll:   :-? 
[/QUOTE]
[http://gaim-encryption.sourceforge.net/](http://gaim-encryption.sourceforge.net/) has all the infomation. It is basically a gaim plugin that encryptions IM messages (both clients must have it).

---

### Post by ubuntu27 on 2005-04-26
Ok, The Installation instruction says that I have to have NSS and NSPR. What are those? And how do I install those for Ubuntu, the example that they provide in [http://gaim-encryption.sourceforge.net/nss.html](http://gaim-encryption.sourceforge.net/nss.html) is for Red Hat:

From: [http://gaim-encryption.sourceforge.net/install.html](http://gaim-encryption.sourceforge.net/install.html)

Source Release version installation instructions. For instructions on installing the CVS version, see the CVS Instructions.

To compile and install the plugin:

    * Make sure you have the NSS and NSPR libraries.
    * Install Gaim, either from source or from a package. If you use a package, make sure to use the development version (gaim-devel-1.2.1-0.i386.rpm, for example) so that the Gaim headers get installed. Note: Debian users- there isn't a gaim-dev package yet, you will need to install from source for now.
    * Download the Gaim-Encryption sources (gaim-encryption-2.36.tar.gz).

---

### Post by TravisNewman on 2005-04-26
if you apt-get installed gaim-encryption you don't need to follow those instructions. apt-get automatically gets the dependencies you need. In order to USE the plugin, all you have to go is load up your gaim prefs, go down to plugins, activate the plugin, and generate the keys (which I THINK it does for you). Then you can talk to others with the plugin in encrypted mode by using the new buttons it gives you in the IM windows.

Since this has deviated from the backport, moving.

---

### Post by ubuntu27 on 2005-04-26
Shikashi (but), the plug-in installed by udo apt-get install gaim-encryption
is version 2.35, which is incompatible with the Gaim Version 1.2.1.

I feel kind embarrasing asking this question, but, how do I update to the new 2.36 ?

I tried sudo apt-get update

but, it didn't download the new version.
And I also tried System/Administration/Ubuntu Update Manager

---

### Post by ubuntu27 on 2005-04-26
Sorry! How Baka (dumb) I was !!
I see, it is not in the respository yet, and our brother jdong wil add to the repositories...

Quote from [http://ubuntuforums.org/showthread.php?t=30010](http://ubuntuforums.org/showthread.php?t=30010)

[QUOTE=jdong]------------------------------------------------------------------------
r119 | rufius | 2005-04-11 23:01:11 -0400 (Mon, 11 Apr 2005) | 2 lines
Changed paths:

Added gaim-encryption 2.36 to Hoary-Staging
------------------------------------------------------------------------

Heh, Rufius, great upload ;) 

I'll add it to the repo tonight.[/QUOTE]

So, that means I have to wait  :-P  hehe. 
Well, go jdong!! Keep up your good job.

Thank you guys for helping me out

---

### Post by ubuntu27 on 2005-04-29
Quote from [http://ubuntuforums.org/showthread.php?t=30010](http://ubuntuforums.org/showthread.php?t=30010)

[QUOTE=jdong]------------------------------------------------------------------------
r119 | rufius | 2005-04-11 23:01:11 -0400 (Mon, 11 Apr 2005) | 2 lines
Changed paths:

Added gaim-encryption 2.36 to Hoary-Staging
------------------------------------------------------------------------

Heh, Rufius, great upload ;) 

I'll add it to the repo tonight.[/QUOTE]
Hey guys...

How do I update to version 2.36 ?  :-?

---

