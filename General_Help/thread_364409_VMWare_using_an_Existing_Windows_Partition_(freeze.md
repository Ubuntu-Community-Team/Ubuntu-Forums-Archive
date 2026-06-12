---
title: "VMWare using an Existing Windows Partition (freeze, unable to boot into Windows)"
date: 2007-02-18
forum: General Help
---

### Post by JesusXP on 2007-02-18
Hi guys!

I recently have tried setting up my vmware for an existing windows partition, however it's running into some problems. My dual boot is set up to use the grub.. So it ends up freezing when trying to boot. Included are two screens showing what the set up looks like, before it freezes. Screenshot 2 is where its frozen. It may be important to note that once I select windows from the grub, I go to "screenshot 2", and then, a windows boot menu comes up, for me to select back into linux, or continue with Windows..

---

### Post by JesusXP on 2007-02-18
I believe I need to get rid of the grub, restore the boot.ini, and use it like that.. Any help?

---

### Post by ignasl on 2007-03-01
I have the same issue. VMWare loads GRUB successfully, but after selecting Windows XP, I get message "Starting up ..." and no activity afterwards. Hitting "Alt + Ctrl + Delete" reboots to GRUB.

If I boot Winodws XP CD, it fails to find the partition with Windows.

Interestingly, Windows XP boots perfectly...

---

### Post by cliss on 2007-03-19
I'm having the same problem: once I select Windows from GRUB, I see "Starting up..." and then the player seems to freeze.

Is there any known workaround for this?  Or am I just doing something wrong?

---

### Post by thieves.honor on 2007-03-27
here is a website full of information on how to get this working.  i followed it through and only came up with a few problems that i was able to work around.  [http://www.motin.eu/www/mirror/physvmware/]("http://www.motin.eu/www/mirror/physvmware/")

---

### Post by KingdomKid on 2007-10-12
I am having the above mentioned issue, after cloning my hard drive with Acronis True Image. 
I can boot into linux fine,.... just get the "starting up..." when trying to select and boot into XP.

I tried to go the link above...the link didnt work???
Anybody figure this out yet?
Thanks

---

