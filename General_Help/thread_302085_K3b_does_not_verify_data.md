---
title: "K3b does not verify data"
date: 2006-11-18
forum: General Help
---

### Post by akudewan on 2006-11-18
Hi,

After upgrading to edgy, I've come across a problem. K3b is not able to verify data after burning CDs. (I always run k3b with sudo)

The burn process runs normally. After that, the CD ejects and reloads. Data verification starts, but k3b is not able to find the very first file on the CD. (and it returns an error)

I have tried different media, and even DVDs. The same problem occurs. Anyone knows why this is happening?

---

### Post by akudewan on 2006-11-22
*bump*

---

### Post by Shay Stephens on 2006-11-22
Just a wild shot in the dark, but have you tried running without using sudo?  I have never had to use that.

---

### Post by akudewan on 2006-11-22
Hi, I tried burning as normal user, but I still get the same error.

---

### Post by Shay Stephens on 2006-11-22
I'm stumped.  Never heard of such a problem.  So I am grabbing from the bottom of the idea barrel here hehehe.  Could you uninstall k3b completely, and then reinstall it?  Perhaps the program has gone wonky?

---

### Post by doobit on 2006-11-22
Here's another stab. K3B verifies data against the original file. It looks at the home directory as default to find the file, but most people (at least I) don't use the home directory itself to store the files we burn, so K3B is looking in the wrong place for the file to verify. Try changing the default path to the directory the file is in in the K3B preferences.

---

### Post by akudewan on 2006-11-28
Hi,

I did a little searching around, and managed to solve a problem.

> 
problem went away for me with enabling the following advanced options:
allow 103 ch. joliet file names
allow 31 ch. iso9660 file names
allow leading periods in iso9660 file names
allow multiple dots in iso9660 file names
**allow lowercase characters in iso9660 file names**

I believe the last one did the trick; char. length limits i had already on, and the dot options i added for caution.

Debian Sarge (stable) with some Etch (testing)
KDE 3.5.4
K3B 0.12.16

YMMV, as always. Good Luck. 


Source: [http://bugs.kde.org/show_bug.cgi?id=119544](http://bugs.kde.org/show_bug.cgi?id=119544)

---

### Post by Shay Stephens on 2006-11-28
Weird!!!  But thank you for posting the fix!

---

### Post by logos34 on 2006-12-05
Success! Thanks for the tip!

---

### Post by Shay Stephens on 2006-12-07
> **akudewan said:**
> Hi,

I did a little searching around, and managed to solve a problem.



Source: [http://bugs.kde.org/show_bug.cgi?id=119544](http://bugs.kde.org/show_bug.cgi?id=119544)

Thank you very much for this info.  As odd as it sounds, I just had the same problem hit me.  I followed the suggestions and it is working again.  Weird huh.

Anyway, thanks a million, I had no hassle getting it to work again :-)

---

### Post by george1984 on 2007-04-07
Hi. I just installed Edgy (I am a computer novice and ignoramus - catching up).

I experienced exactly the same verification problem.

I enabled Akudewan's advanced options, and hey presto K3b is now OK.

I would have never guessed. As a paranoid backer-upper, I am truely grateful for the help.

---

