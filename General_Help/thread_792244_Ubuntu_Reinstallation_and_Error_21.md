---
title: "Ubuntu Reinstallation and Error 21"
date: 2008-05-12
forum: General Help
---

### Post by jamieh on 2008-05-12
I have learned (the hard way, GAAAH!!) that if you reinstall an OS (with GRUB as your bootloader), you get an "Error 21", and you are locked out.

I want to ditch Ubuntu (Sorry, GNOME just isn't for me), and install Kubuntu from scratch (I screwed up my Ubuntu install bad, and it just isn't worth fixing when I can just zero the drive and start over).

Anyway, my questions:

(1): When I replace my screwed-up Ubuntu with Kubuntu, how do I prevent an Error 21 from happening? (I dual-boot with Windows, and I don't want to lose the Windows Install)
[COLOR="Blue"]Please tell me, will this work to answer Question (1)?

**Step One:** Disconnect Ubuntu drive
**Step Two:** Boot up to see the dreaded Error 21
**Step Three:** Do [this]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console")
**Step Four:** Shut down computer
**Step Five:** Reconnect Ubuntu drive
**Step Six:** Boot Kubuntu CD and install over Ubuntu, and reinstall GRUB over the Windows bootloader, like I did when I installed Ubuntu
**Step Seven:** Reboot to a fully-working dual-boot of Kubuntu and Windows XP

Is there an easier way?[/COLOR]

(2) How can I get Compiz Fusion to work in Kubuntu?

Thanks for all your help!
jamieh

---

### Post by jamieh on 2008-05-12
Also, I read that the KDE 4.0 Kubuntu is quite buggy, even though it is a final release?
Should I use KDE3 or KDE4?
Thanks again!

---

### Post by Tomatz on 2008-05-13
Hi jamieh

You can install kubuntu while in ubuntu by simply opening a terminal and typing:


```
sudo apt-get install kubuntu-desktop
```

Logout and change session to KDE


If you install it either in this way or via the disc you will still have the same problem with your gpu drivers/compiz because the drivers are exactly the same.

Suppose its worth a try. You could always install the drivers the way i mentioned in the other thread after installing kubuntu.

;)

Also the error 21 is just grub saying that it cant boot the selected partition.  If this happens just go back to the first grub screen and press **"e"** on the entry you want to boot then **"e"** again on the first line (e.g. hd0,1) and change the 0,1 part to the correct HDD partition. 

[I]E.g. for the first partition on your primary drive it should not be:
[/I]
**hd0,1**

_It should be_

**hd0,0**

_These drive numbers are just examples your system will probably be different_

Once you have edited it correctly press enter then boot.

These changes will not be persistent so after you will need to edit your /boot/grub/menu.lst file accordingly.

---

### Post by jamieh on 2008-05-13
> **Tomatz said:**
> Hi jamiehYou can install kubuntu while in ubuntu by simply opening a terminal and typing...

Yeah I know, but Envy screwed up my install pretty bad. Whenever I log in, everything seems to be working fine, but no programs start when I try to open them, and there are no icons in the system tray, and the internet doesn't work :(

---

### Post by jamieh on 2008-05-13
> Also the error 21 is just grub saying that it cant boot the selected partition

There is no Grub Boot Menu, it goes straight from POST to "Error 21" :(

---

### Post by Nythain on 2008-05-13
when you install kubuntu, just nuke all the ubuntu/linux partitions (making sure to keep your window partitions intact), recreate them and slap grub in the MBR... should do the trick as long as you didn't jack with priorities and whatnot in your bios

---

### Post by Tomatz on 2008-05-13
Keep pressing escape during the post (just after) to see if you can get the grub menu up.


Alternitavly download this:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Download the .iso and burn to disc. It is basically grub on a cd. It also allows you to reinstall grub and the xp bootloader.

;)

---

