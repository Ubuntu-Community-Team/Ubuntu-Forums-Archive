---
title: "Custom Install of Linux Mint"
date: 2007-06-07
forum: General Help
---

### Post by floweringmind on 2007-06-07
I want to install Linux Mint which is based off of Ubuntu. How can I modify the installer so it installs from the Linux Mint ISO instead of downloading the Ubuntu ISO?

Thanks!

Chris

---

### Post by ago on 2007-06-07
> **floweringmind said:**
> I want to install Linux Mint which is based off of Ubuntu. How can I modify the installer so it installs from the Linux Mint ISO instead of downloading the Ubuntu ISO?

Thanks!

Chris

You need

1. to provide a metalink file pointing to the alternate iso
2. edit wubi/src/inspector/IsoList.ini and add an entry 
3. add the entry to the listbox in wubi/src/pages/main.ini

Feel free to rebrand but don't forget to do a bit of pubblicity for us ;)

---

### Post by mpgarate on 2007-06-07
im not sure what youre asking.. you can downlaod the linux mint installer iso here

[http://linuxmint.com/download.html](http://linuxmint.com/download.html)


i dont believe you can modify the ubuntu iso to install linux mint (easily)

im using linux mint right now to type this post, and my general opinion of it is, its ubuntu with a spicier theme, and cool plugins and codecs pre installed.

edit: oh woops. I guess he  know more what youre asking

---

### Post by floweringmind on 2007-06-08
Thanks! so much!

---

### Post by parrotty on 2007-10-15
This post was unclear to me, but sounds like it may solve my problem.  I have a vostro 1400 and want Linux Mint on it.  Ubuntu 7.10 RC1 boots, but Linux Mint gives me some tty error almost instantly after the menu selection (from what I read it's a motherboard issue).

So, is there a way to boot up the Ubuntu live-cd and then do a network install of Linux Mint and use the ubuntu driver set?  Or any work around for the vostro 1400?

Thanks in advance.

---

