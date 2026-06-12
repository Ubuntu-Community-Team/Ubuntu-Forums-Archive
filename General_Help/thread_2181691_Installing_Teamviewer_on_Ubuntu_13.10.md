---
title: "Installing Teamviewer on Ubuntu 13.10"
date: 2013-10-18
forum: General Help
---

### Post by fsdemir on 2013-10-18
Hi,

I have upgraded to Ubuntu 13.10 (64 bit). When I try to install Teamviewer I get the following error:

```
>sudo dpkg -i teamviewer_linux_x64.deb 

Selecting previously unselected package teamviewer.
(Reading database ... 231622 files and directories currently installed.)
Unpacking teamviewer (from teamviewer_linux_x64.deb) ...
dpkg: dependency problems prevent configuration of teamviewer:
 teamviewer depends on lib32asound2; however:
  Package lib32asound2 is not installed.
 teamviewer depends on ia32-libs; however:
  Package ia32-libs is not installed.

dpkg: error processing teamviewer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 teamviewer

```

I've tried to manually install dependencies but apt-get can't find candidates for them. I was able to install Teamviewer on Ubuntu 13.04 so I guess the problem is about some packages being deprecated in Saucy.

Is there any workaround?

Thanks.

---

### Post by GWBouge on 2013-10-18
I ran into this as well.  The details are a bit over my head, but 13.10 has multiarch support and no longer includes the 32-bit libraries in the repos.  Try using the 32-bit/Multiarch version of Teamviewer, it installed flawlessly for me.

[http://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx#multiarch]("http://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx#multiarch")

---

### Post by chsados2 on 2013-10-19
I kept on getting the following error:
```

Removing libexif12:i386 ...
/var/lib/dpkg/info/libexif12:i386.postrm: 1: /var/lib/dpkg/info/libexif12:i386.postrm: libcups: not found
dpkg: error processing libexif12:i386 (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 libexif12:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So I had to manually remove the file:

```
cd /var/lib/dpkg/info/
sudo rm -f libexif12:i386.postrm
```

Then ran:

```
sudo apt-get update && sudo apt-get install -f && sudo apt-get update
```

TeamViewer now working in 13.10 \\:D/

---

### Post by rogelio1234 on 2014-02-11
I'm sorry to ask but:

Which teamviewer version did you install?

I have a license for version 7, but i'm having exactly that problem with the same libraries

I'll give a shot to your solution and i'll post the results later.

Thanks!

---

### Post by rogelio1234 on 2014-02-11
For as incredible as it sounds, it has to fail before it works.

Teamviewer 7 For Ubuntu 13.10 64 bits:
- Download the 32 bit DEB version 
- Deploy it from terminal (type: sudo dpkg -i teamviewer_linux.deb)
- If it worked, then congrats, if it returns the lib missmatch type: sudo apt-get install -f
- Deploy it again (sudo dpkg -i teamviewer_linux.deb)

It worked like a charm for me !

Thanks a lot guys!

---

### Post by Xubuntist on 2014-03-24
> **rogelio1234 said:**
> For as incredible as it sounds, it has to fail before it works.

Teamviewer 7 For Ubuntu 13.10 64 bits:
- Download the 32 bit DEB version 
- Deploy it from terminal (type: sudo dpkg -i teamviewer_linux.deb)
- If it worked, then congrats, if it returns the lib missmatch type: sudo apt-get install -f
- Deploy it again (sudo dpkg -i teamviewer_linux.deb)

It worked like a charm for me !

Thank you for that easy to follow process. 
It worked like a gem for me, first time :)

Thank you

---

### Post by AFriendlyNerd on 2014-04-06
For future searchers, same thing happened to me after the upgrade. This worked quickly and easily for me on 13.10 64-bit: [URL="http://iqbalnaved.wordpress.com/2014/01/04/installing-teamviewer-9-on-64-bit-ubuntu-13-10/"]http://iqbalnaved.wordpress.com/2014/01/04/installing-teamviewer-9-on-64-bit-ubuntu-13-10/

[/URL]

---

### Post by kdavies on 2014-11-27
Hi

I am on ubuntu 13.10 and found this worked ok
Download version 9 with out multi arch
use gedbi to install it.
Sweet

---

