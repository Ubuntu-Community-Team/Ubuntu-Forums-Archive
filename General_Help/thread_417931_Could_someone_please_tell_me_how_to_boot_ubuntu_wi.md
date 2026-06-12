---
title: "Could someone please tell me how to boot ubuntu with using the live cd?"
date: 2007-04-22
forum: General Help
---

### Post by Ndonato on 2007-04-22
Alright so I downloaded and installed linux onto my machine and installed it onto a spare drive that i really didn't care about. and now I want to know how to boot ubuntu without constantly having the live cd in the drive. Thanks!

---

### Post by Toadmund on 2007-04-22
I don't understand, if you have it installed onto HD, you don't need the CD at all.

Please explain better.

---

### Post by desheikh on 2007-04-22
Hi,

If you remove the live cd from your pc the ubuntu bootloader should just appear and allow you to pick the os you want to run.. doesnt that happen?

The spare drive you installed to isnt an external one by any chance?

---

### Post by Ndonato on 2007-04-22
ok. I booted from the live cd and installed linux onto a spare INTERNAL drive. when i set the boot priority in the BIOS to that drive, linux would not boot. so now, i can't boot linux without the cd. and the drive that it's on is used for games in. My other drive is running XP.

---

### Post by hikaricore on 2007-04-22
The live cd does not boot your installed copy of linux, it only boots the live environment.

Grub boots the installed copy of ubuntu or windows via the selection menu.

---

### Post by Hellion DarkLord on 2007-04-22
By default, I think, The boot loader for linux is installed in the MRB or first sector of the primary hard drive.  If you selected something else when you installed Ubuntu, then you have to use that particular disc and drive sector in order to boot to Ubuntu.  

I would try the installation again, but before that, try booting to the primary drive and see if the Grub boot loader comes up.  If not try another drive if you have one.  

Be very certain that you install the boot loader on the drive you want to boot to if you do need to install it again.  This is important if you want to be able to use your cdrom drive while you are running linux.  I have made this mistake before, but I can't remember if you can indeed reinstall the boot loader if you need to without doing a complete installation.

Sorry I couldn't be more helpful.

---

### Post by nasos on 2007-04-22
> **Ndonato said:**
> ok. I booted from the live cd and installed linux onto a spare INTERNAL drive. when i set the boot priority in the BIOS to that drive, linux would not boot. so now, i can't boot linux without the cd. and the drive that it's on is used for games in. My other drive is running XP.

Bring your BIOS setup in the initial state, as it was after you installed ubuntu. It should get to the MBR where grub is loading.
Can you reboot in your windows at all?

---

