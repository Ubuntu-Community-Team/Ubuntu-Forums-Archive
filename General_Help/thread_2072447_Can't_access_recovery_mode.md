---
title: "Can't access recovery mode"
date: 2012-10-17
forum: General Help
---

### Post by AussieGuy on 2012-10-17
I need recovery mode to fix up my sudoers file (and add muself - the only user, back into it).  However, I simply can't get the menu  which allows me to log into recovery mode.  No matter where I press Shift, or Esc during the boot process, the screen goes blank, then after I while I get the splash login screen.  I can't modify the grub settings (as that would require sudo, fron which I'm currently locked out) - is there, for example, a BIOS setting I can change?  I can access a BIOS screen with Ctrl-S during boot up, but I need the next screen beyond that, which I can't get to.

I suppose I could boot from a recovery CD... but that seems a little extreme.  How can I access the boot menu which includes the recovery mode item?

Thanks,
-A.

---

### Post by sienile on 2012-10-17
I think you're supposed to hold Shift during boot to unhide GRUB.

I would just edit the sudoers through a LiveCD if you can't get it to work.

---

### Post by AussieGuy on 2012-10-18
Thanks for your response to my query.  I logged in using the ubuntu-rescue-remix cd, and mounted my boot partition /dev/sda1 to /mnt. My /etc/sudoers files seems OK, and so I tried the command

sudo usermod -a -G sudo AussieGuy

only to be told that "AussieGuy" wasn't a recognized user.  So I tried

sudo chroot /mnt

only to obtain the error

"chroot: failed to run command '/bin/bash': Exec format error"

which I understand could be caused by a conflict between the 32-bit rescue cd and my 64-bit system.  

I'm now downloading the live 64-bit ubuntu iso image (all 694Mb) of it, and I'll see how I go with that.

It all seems a bit complicated though - just to add myself back into the sudo group!

-A.

---

