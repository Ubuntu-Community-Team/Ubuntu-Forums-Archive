---
title: "libmjpegtools0 problem, broken"
date: 2006-08-12
forum: General Help
---

### Post by OrganicPanda on 2006-08-12
Hey I added the "deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sarge main" repository because I'm trying to get WMV9's to play and I heard that repository had the newest VLC etc etc but it goes crazy when I try to install libmjpegtools0 which is needed as far as I can tell, I get:

```

panda@panda-desktop:~$ sudo aptitude install libmjpegtools0
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  mjpegtools
The following NEW packages will be installed:
  libmjpegtools0
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/214kB of archives. After unpacking 545kB will be used.
Writing extended state information... Done
(Reading database ... 160040 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.3sarge1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.3sarge1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.3sarge1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libmjpegtools-dev:
 libmjpegtools-dev depends on libmjpegtools0 (= 1:1.8.0-0.3sarge1); however:
  Package libmjpegtools0 is not installed.
dpkg: error processing libmjpegtools-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmjpegtools-dev

```

Any Ideas?

---

### Post by OrganicPanda on 2006-08-15
that's a no then? :p

---

### Post by andars on 2006-08-19
I had this problem installing cinelerra:

sudo apt-get install libquicktime0
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb

---

### Post by OrganicPanda on 2006-08-23
I'm so glad someone replied but when I try that I get:

```

panda@panda-desktop:~$ sudo apt-get install libquicktime0
Reading package lists... Done
Building dependency tree... Done
libquicktime0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
panda@panda-desktop:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb
panda@panda-desktop:~$

```

---

### Post by dovicka on 2006-08-29
PLEASE someone help. libmjpegtools0 1.1.8/0 seems to be missing from the whole internet. other files like libguicast could be found where I got the cinerella deb file even though google found nothing, but libmjpegtools0 is nowhere to be found either place!! anybody have it? cause I need to make a video and I need cinerella

---

### Post by OrganicPanda on 2006-08-29
I am desperately seeking the answer too, Nothing seems to be working

---

### Post by perky on 2006-09-16
I'm getting the same thing...could this be something to do with BUMPS?

---

### Post by Anduu on 2006-09-16
Basically what is happenning is by using Debian repos you are trying to install files which are not compatible with nor available from Ubuntu's repos.

It is looking for dependencies which Ubuntu cannot satisfy thus it won't install.

If your multimedia codecs are installed correctly wmv9 should not be a problem.

Try Automatix

---

### Post by Boguz on 2007-12-08
i think i have kind of the same problem (well, maybe exactly the same problem with the*** libmjpegtools0*** file)

When i try to install CINELERRA or LiVES (both from the Synaptic), it first asks "Mark additional  required changes?" [SIZE="2"](and it shows everything else we need to install so the software will work.)[/SIZE]
I mark YES and then i get the error:

[I]lives:
 Depends: libmjpegtools0 but it is not going to be installed[/I]

I looked for this file and i had installed the "libmjpegtools0c2a".
i thought this was some kind of incompatibility problem, so i uninstalled this one and tried to install from synaptic the "libmjpegtools0", but i get this error:

[I]libmjpegtools0:
 Depends: libquicktime0 (>=0.9.10+debian) but it is not installable[/I]

Does anyone have an idea of what is going on?
I would really need to get one of this softwares to work.
Any ideas?

Thank you

---

### Post by aonegodman on 2008-01-10
I'm having same issues trying to install tovid onto my system. Same replies as above.

Package Manager told me it would have to remove avidemux, dvdstyler and a few others. I said ok.

But then it had issues with the " lib "  dependencies.

Is there a fix anyone?

---

### Post by hobong on 2008-06-16
In my case I'm doing 
$sudo aptitude install cinelerra 
and then I answere no for dependency
it could install cinerrela

i'm using ubuntu hardy heron 8.04 and get cinerrela from here :
[http://cinelerra.org/getting_cinelerra.php#apt](http://cinelerra.org/getting_cinelerra.php#apt)

---

### Post by Anduu on 2008-06-16
Errr this post is almost 2 years old :confused:

---

### Post by Detox06 on 2008-06-16
> **Anduu said:**
> Errr this post is almost 2 years old :confused:

And yet its still an issue. And an unsolved one, from what I read. 

I have a laptop and a desktop both running ubuntu 8.04. I have upgraded them both from fresh install of 7.04 > 7.10 > 8.04. The desktop is having this problem, and the laptop is not, even though they both have the same programs installed. (the laptop probably more, because I use it more often)

I would love to fix this. It just started happening about a week ago, and nothing I do can fix it.

---

