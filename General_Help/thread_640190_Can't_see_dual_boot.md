---
title: "Can't see dual boot"
date: 2007-12-13
forum: General Help
---

### Post by Drethon on 2007-12-13
I'm trying to run Wubi on a new lenovo laptop with Vista installed.  I think everything is installed find but the dual boot screen goes by so fast I can't touch it.  I'm fairly new at this, can anyone tell me how to address this?

Thanks

---

### Post by Schalken on 2007-12-13
perhaps the timeout has been set to a very low value. in ubuntu run "sudo gedit /boot/grub/menu.lst", look for the "timeout" option change it something sane like "timeout 5", save and reboot.

---

### Post by Drethon on 2007-12-14
Only problem is it defaults to windows, not Ubuntu.  Where do I find the grub boot options in windows?

---

### Post by Drethon on 2007-12-15
I did find the file C:\wubi\boot\grub\menu.lst, but updating it doesn't seem to have an effect.  Is there a script to run to update the bootloader?

And if its the program C:\wubi\boot\winboot\wubildr, this program crashes when I try to run it in windows.

---

### Post by clive_pearce on 2007-12-16
If the timeout in the boot ini file is set too low, get to it through windows. 

:)

---

### Post by ago on 2007-12-17
In vista use easybcd to see the boot options. 
Wubi 7.04 and Wubi 7.10 have slightly different setups

---

### Post by Drethon on 2007-12-17
Never knew about easybcd, I'll give that a shot when I get home.  I also found information about using a rescue cd to update the boot settings.  easybcd looks like it should resolve my issues but if not I'll try the rescue cd.

Thanks for the info!

---

### Post by clive_pearce on 2007-12-17
Did you edit the boot ini file through windows?

---

### Post by Drethon on 2007-12-17
easybcd worked, now to learn how to actually use linux for everything I want to do...

Thanks for the help!

---

