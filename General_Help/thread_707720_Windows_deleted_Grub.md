---
title: "Windows deleted Grub?"
date: 2008-02-25
forum: General Help
---

### Post by twodayslate on 2008-02-25
I recently installed Windows XP on a second hard drive and now I can not boot to ubuntu. 

I even tried to boot with the XP HD not plugged in but I got a black screen. I have some access to the files via the [http://www.fs-driver.org/](http://www.fs-driver.org/) program.

Did grub get deleted or something? Why cant I use by linux?
thanks

---

### Post by The Cog on 2008-02-25
It does that.

Use your Ubuntu CD and choose to rescue your ubuntu system. Then use the command 
sudo grub-install /dev/sda
which should replace grub.

---

### Post by bodhi.zazen on 2008-02-25
Yep :(

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by twodayslate on 2008-02-25
Thank you so much guys!

---

