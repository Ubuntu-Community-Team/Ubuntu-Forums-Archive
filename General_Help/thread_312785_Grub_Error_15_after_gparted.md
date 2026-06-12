---
title: "Grub Error 15 after gparted"
date: 2006-12-04
forum: General Help
---

### Post by deviantintegral on 2006-12-04
I recently used gparted's live cd to do some major repartitioning (and man, is that disc concentrated awesome!). Everything worked fine, except for my custom Grub setup. My system is dual boot and has grub set up as shown in the following article:

[http://www-128.ibm.com/developerworks/linux/library/l-osswitch/index.html](http://www-128.ibm.com/developerworks/linux/library/l-osswitch/index.html)

The problem that I have is that if I manually load from the first instance of the bootloader (which is "normal"), things work fine. However, if I boot from the "control" loader, grub complains about Error 15 "File not found". I redid grub-install to drop in stage1.5 and the like, with no effect. So any suggestions as to how I can fix this?

Thanks,
--Andrew

---

### Post by Sef on 2006-12-05
From the [Gentoo GRUB]("http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap6") error message:

> 15. Missing Grub Image

Situation

When booting the system, you do not see that spify Gentoo splashscreen.

Solution

First of all check if the splashscreen file you are referring to in your grub.conf really exists. If that is the case, go and check the grub ebuild. Maybe the patch for the splash image is commented out in the version that you are using. 

---

### Post by deviantintegral on 2006-12-05
I don't have a spashimage defined - however, neither of my grub loaders now show the verson/information header at the top like they used to.

I get the error once I try to boot any image from the 2nd menu.

---

