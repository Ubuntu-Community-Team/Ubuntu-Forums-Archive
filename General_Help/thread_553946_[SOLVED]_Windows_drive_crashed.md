---
title: "[SOLVED] Windows drive crashed"
date: 2007-09-18
forum: General Help
---

### Post by dpar on 2007-09-18
Ok, heres the problem......:(

My Windows hard drive has bit the dust.\\:D/

Problem: Along with it it took my grub menu on the MBR.
Ubuntu is on a seperate drive, but I can't boot it without grub.

Can I reinstall grub to the ubuntu drive without screwing anything up? And how,exactly?
I really don't want to mess it up, because it would be a pain to restore all that info from backups:(

I'm currently using the LiveCD for internet access(god I love those LiveCDs!!!)

---

### Post by forestpixie on 2007-09-18
you should be able to do that with the live cd

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

hope that helps

or maybe download and burn [supergrub]("http://supergrub.forjamari.linex.org/?section=download")

---

### Post by dpar on 2007-09-18
Thanks forestpixie, I found that thread and did that stuff, but........
I might have made things a little more difficult:(

When my drive crashed, I moved the connections to put the Ubuntu drive in the master position. I have my grub back now but it is trying to load Ubuntu from HD1,0 when it is now hd0,0.

I realize I will probably have to edit menu.lst, but how do I sudo from the livecd to edit the menu.lst on the hard drive?


Edit: Stupid me.......I got it fixed. I guess I should have done a proper search](*,)
Just had to creat a media directory for the drive and edit the menu.lst from there. Thanks

For those interested, I used this thread.....[http://ubuntuforums.org/showthread.php?t=539482&highlight=remove+windows+drive](http://ubuntuforums.org/showthread.php?t=539482&highlight=remove+windows+drive)

---

