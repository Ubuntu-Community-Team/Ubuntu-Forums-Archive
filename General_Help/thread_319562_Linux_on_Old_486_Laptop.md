---
title: "Linux on Old 486 Laptop"
date: 2006-12-15
forum: General Help
---

### Post by wireddad on 2006-12-15
Hello,

Does any one know of linux os that will run on an old 486 laptop?  Trying to revive one in hope that it will be usable for kids.  Thanks.

---

### Post by Portable_Jim on 2006-12-15
> **wireddad said:**
> Hello,

Does any one know of linux os that will run on an old 486 laptop?  Trying to revive one in hope that it will be usable for kids.  Thanks.
try this: [http://mypage.uniserve.ca/~thelinuxguy/small_and_floppy_linux/all.html]("http://mypage.uniserve.ca/%7Ethelinuxguy/small_and_floppy_linux/all.html")

---

### Post by wireddad on 2006-12-15
I think Knoppix may work.  I do not think Ubuntu will install.  Thoughts?

---

### Post by wireddad on 2006-12-15
> **Portable_Jim said:**
> try this: [http://mypage.uniserve.ca/~thelinuxguy/small_and_floppy_linux/all.html]("http://mypage.uniserve.ca/%7Ethelinuxguy/small_and_floppy_linux/all.html")



Thanks.  I will check this out.

---

### Post by ibanez on 2006-12-15
a few distros for old hardware

[http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

---

### Post by fragos on 2006-12-15
Puppy and DSL do well on older hardware.

---

### Post by wireddad on 2006-12-15
Thanks all.

---

### Post by wireddad on 2006-12-16
Ok, loaded (Toshiba Satellite 315CDS, 486DX, 64 RAM, 12G HD)
Knoppix - did not like the 64 RAM.  Would not load windows manager.
DeliLinux - would not load windows manager
Finally, Puppy Linux - installed and working.  Issue, can not get the keyboard layout right--yet.  Looks nice.

I need the click and go thing since I am not command line literate. :rolleyes:

Does Ubuntu have a version that will work on such a system?

---

### Post by wireddad on 2006-12-16
May be Xubuntu.  Has anyone try it on an old system?

---

### Post by wireddad on 2006-12-17
Xubuntu did not work on this system of mine.  It would not complete loading--after all night of trying.  Oh well.

---

### Post by Sef on 2006-12-17
> Xubuntu did not work on this system of mine. It would not complete loading--after all night of trying. Oh well.

Check out [Fluxbuntu]("http://wiki.fluxbuntu.org/index.php?title=Main_Page").  It is based on Ubuntu.

---

### Post by wireddad on 2006-12-17
I will.  Looks like it is still developing.  I will download it when ready.  I definitely would like to stay with the Ubuntu platform.  Just seems simpler than others.  Thanks.

---

### Post by Sef on 2006-12-17
Fluxbox is the lightest of the lightweight window manager.   Here's an page in [Ubuntu's documentation]("https://help.ubuntu.com/community/Fluxbox") that tells how to install Fluxbox.  Just do a server install first.

You're welcome.

---

### Post by fragos on 2006-12-17
Most laptops have two memory slots.  You may be able to upgrade your memory.

---

### Post by wireddad on 2006-12-17
> **fragos said:**
> Most laptops have two memory slots.  You may be able to upgrade your memory.

Oh nooooo.  I birth it back in 98.  I believe I have already upgraded it--the HD has been upgraded for sure.  I will verify.  If so, hopefully it will be cheap.

---

### Post by wireddad on 2006-12-17
> **Sef said:**
> Fluxbox is the lightest of the lightweight window manager.   Here's an page in [Ubuntu's documentation]("https://help.ubuntu.com/community/Fluxbox") that tells how to install Fluxbox.  Just do a server install first.

You're welcome.

I am not well versed in Linux yet.
Can I install this using PuppyLinux?

---

### Post by K.Mandla on 2006-12-26
I should think so. I'm not well versed in Puppy, so I might be wrong.

DSL will install to a hard drive, and uses Fluxbox by default. You might try that.

---

### Post by DarkN00b on 2006-12-26
Check out the [MiniLinux Wiki]("http://en.wikipedia.org/wiki/MiniLinux"), there are lots of options there. I'm currently getting ready to try an install on the oldest machine I've ever tried: 486-66 w/16MB ram. I'm looking at DSL or one of the distros on the Wiki I mentioned above. DSL might be too large though. :)

---

### Post by wireddad on 2006-12-30
> **DarkN00b said:**
> Check out the [MiniLinux Wiki]("http://en.wikipedia.org/wiki/MiniLinux"), there are lots of options there. I'm currently getting ready to try an install on the oldest machine I've ever tried: 486-66 w/16MB ram. I'm looking at DSL or one of the distros on the Wiki I mentioned above. DSL might be too large though. :)

So, what worked for you?

---

### Post by DarkN00b on 2006-12-30
> **wireddad said:**
> So, what worked for you?

Heh, I've been too busy to try. My job has me kinda jumping right now.

---

### Post by Sef on 2006-12-31
I would look at [Vector Linux]("http://vectorlinux.com").  It is made to run on older hardware and is based on Slackware.

---

### Post by Portable_Jim on 2006-12-31
How about DeLi Linux (Desktop Light Linux) - [http://delili.lens.hl-users.com/](http://delili.lens.hl-users.com/)

---

### Post by Lord Illidan on 2006-12-31
DSL should work nice.

---

### Post by wireddad on 2006-12-31
Since I am new to this Linux thing i really like the fact that Ubuntu auto configure most things for me....like automount drives--including usb flash drives.  Do most linux distro configure that same as Ubuntu? :D  For beginners like me that is.  I loaded PuppyLinux, and loaded fine, but did not notice, yet, if it will recognize plug and play type media.

---

### Post by fragos on 2006-12-31
Linux has good support for many devices without having to install special drivers.  USB storage is well recognized by Linux and for the most part automounted for you.  When removing a USB storage device you should perform an eject to insure all data cached to be written to the drive is before you remove it.  It's common for linux distros to show a device icon on your desktop when a USB storage device is detected.  Right click that icon for the drop down menu which should include an eject command.

---

### Post by AgenT on 2006-12-31
The problem is that most very slim distributions, like DSL, use the 2.4 and not the newer 2.6 kernel. The 2.6 kernel along with a few utilities enables automatic device usage. 2.4 does it too, but 2.6 is better. The reason for slim distributions using 2.4 is due to size: 2.4 has a smaller size than 2.6.

---

