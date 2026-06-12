---
title: "mplayer wrong language"
date: 2006-09-23
forum: General Help
---

### Post by nik on 2006-09-23
After a recent update, my mplayer suddenly displays all menus in Italian... I'd really like to get it back to English. Anyone had this happen? There was an error message about something with mplayer during the upgrade, can't remember what... But it works fine.

---

### Post by ayoli on 2006-09-23
try to remove/reinstall it

---

### Post by nik on 2006-09-23
No joy...

But at least I got the error message:

E: mplayer: subprocess post-installation script returned error exit status 2

Doesn't really tell me anything...

It might be because I've had to force versions on some other packages, but I can't remember which...

Kind of annoying, because mplayer is the only one I can use fullscreen with aiglx/compiz...

---

### Post by ayoli on 2006-09-23
then try:
```
sudo apt-get -f install
```

---

### Post by nik on 2006-09-23
Well, here's the output:

nik@nik-laptop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mplayer (0.99+1.0-pre8-0ubuntu1) ...
Can't locate ConfHelper.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /var/lib/dpkg/info/mplayer.postinst line 5.
dpkg: error processing mplayer (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mplayer
E: Sub-process /usr/bin/dpkg returned an error code (1)

tried reinstalling perl, but no use. So I ended up downgrading mplayer and locking it. Works fine again. Just have to remember... :)

---

### Post by plast on 2006-09-23
ConfHeler is in libconfhelper-perl package.

But even with that there are some problems:
1) italian version of mplayer instead of english (I saw someone else posting on this forum with that problem earlier),
2) lirc doesn't work properly.

Downgrading solves both these problems of course.

---

### Post by Treviño on 2006-09-25
To get the package configured, please, install the package libconfhelper-perl, then dpkg --configure -a

Anyway I'm fixing that package...

---

### Post by Treviño on 2006-09-25
> **Treviño said:**
> To get the package configured, please, install the package libconfhelper-perl, then dpkg --configure -a

Anyway I'm fixing that package...
Try new version now, please.
You'll find it at [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)

Anyway also if I've compiled it with language="en", I'm not sure that the language "bug" is fixed...
Let me know!

Another thing... The configuration problem has been fixed and, let me know if you need the lirc support (or any other).

Bye and thanks for bugfixing ;)

---

### Post by nik on 2006-09-25
Getting dependency problems now...

mplayer:
  Depends: libfaac0 (>=1.24+cvs20060416) but 1.24clean-0ubuntu4 is to be installed

I didn't even remember that this was from your repo... thanks for providing it, and all the other great packages :)

---

### Post by Treviño on 2006-09-25
I converted that from the debian-multimedia packages repository, anyway I'll fix the mplayer package to work with standard ubuntu too...

---

### Post by Treviño on 2006-09-25
Now it should work correctly... Isn't it?
Anyway I've compiled also the latest svn version available...

If you want, I could add that instead of the latest &#8220;stable&#8221;....

---

### Post by nik on 2006-09-25
well... couldn't get it with apt-get, got a size mismatch error. downloading and installing with dpkg works fine, but still in italian... maybe I should just learn italian :)

Don't really care about the version, unless is some significant improvement in the svn?

---

### Post by Treviño on 2006-09-25
From a first look I don't see great improvements... Btw works fine, and I've enabled the support for lirc...
The only thing that I've noticed that doesn't support the Divx4linux, btw it decodes them well using w32codecs I think...

Regarding my package... It's really strange to hear that it's still in italian, becouse all the compilation settings are good...

I'll retry with a new compilation tree...

---

### Post by skoruppa on 2006-09-26
yeah i got a mplayer in italian to :P

---

### Post by Treviño on 2006-09-27
> **skoruppa said:**
> yeah i got a mplayer in italian to :P
Now it should be fixed...
Update the apt database and Upgrade your distro ;)

---

### Post by nik on 2006-09-27
Working nicely :)

Thanks a lot!

---

### Post by skoruppa on 2006-09-27
yes, now working :)

---

### Post by Treviño on 2006-09-27
Good... Happy to know...
If you want I've packaged also version from latest SVN... It's not in my repository, but you can download it from:
- [http://www.fastdump.net/818222](http://www.fastdump.net/818222) (mplayer) 
- [http://www.fastdump.net/23362](http://www.fastdump.net/23362) (mencoder) 

BYE! ;)

---

