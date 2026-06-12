---
title: "Remove w10"
date: 2019-08-16
forum: General Help
---

### Post by dtree46 on 2019-08-16
I ran ubuntu for years.
Changed to w10 in order to run Fusion 360.
Now, I need to get rid of w10.
How can the EFI boot up be bypassed, removed, deleted?
 F9 nor F10 work on my Hp Eveny.

Yes, I read a few post.

---

### Post by crip720 on 2019-08-16
If I am reading this right, you are saying you can't get into bios settings to be able to boot from usb first.  There is a way to get into bios from windows, but I am sure how to do it.  I think it is from windows troubleshooter or repair section.   Here is one site from google.  [https://www.laptopmag.com/articles/access-bios-windows-10](https://www.laptopmag.com/articles/access-bios-windows-10)

---

### Post by Autodave on 2019-08-17
To get into the BIOS, try the ESCAPE key while booting.  Turn machine on and instantly start smacking the ESCAPE key.

---

### Post by yancek on 2019-08-17
You should be able to access the BIOS settings with Esc key then F10 to make the change.  The link below (the last post) explains using efibootmgr to remove an EFI entry.  Some times the efibootmgr does not work (my experience) in which case you will need to do it in the BIOS.

 [https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Remove-additional-UEFI-OS-boot-managers-from-bios-boot/td-p/6587433](https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Remove-additional-UEFI-OS-boot-managers-from-bios-boot/td-p/6587433)

---

### Post by dtree46 on 2019-08-17
> **crip720 said:**
> If I am reading this right, you are saying you can't get into bios settings to be able to boot from usb first.  There is a way to get into bios from windows, but I am sure how to do it.  I think it is from windows troubleshooter or repair section.   Here is one site from google.  [https://www.laptopmag.com/articles/access-bios-windows-10](https://www.laptopmag.com/articles/access-bios-windows-10)

Did the instructions at the website.
After entering the last 'Restart' button, screen went black and remained that way.
Waited 5 minutes before restarting w10.

Any ideas as to why this did not work or waiting longer does?

---

### Post by dtree46 on 2019-08-17
> **Autodave said:**
> To get into the BIOS, try the ESCAPE key while booting.  Turn machine on and instantly start smacking the ESCAPE key.

Did this by tapping ESC key then by holding it down.
Neither worked.

Any other ideas.

---

### Post by dtree46 on 2019-08-17
> **yancek said:**
> You should be able to access the BIOS settings with Esc key then F10 to make the change.  The link below (the last post) explains using efibootmgr to remove an EFI entry.  Some times the efibootmgr does not work (my experience) in which case you will need to do it in the BIOS.

 [https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Remove-additional-UEFI-OS-boot-managers-from-bios-boot/td-p/6587433](https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Remove-additional-UEFI-OS-boot-managers-from-bios-boot/td-p/6587433)

Ubuntu is not installed yet.

---

### Post by dragonfly41 on 2019-08-17
Possibly [F10 for HP bios]("https://support.hp.com/gb-en/document/bph07110") when booting up ??

---

### Post by dtree46 on 2019-08-17
> **dragonfly41 said:**
> Possibly [F10 for HP bios]("https://support.hp.com/gb-en/document/bph07110") when booting up ??

F10 doesn't work because of w10 quick start boot up.

---

### Post by dragonfly41 on 2019-08-18
Brute force idea is to substitute existing drive (containing W10 etc.) with a spare formatted drive and then try to access BIOS.
It might be easier to start afresh with the new drive, install fresh Ubuntu, attach the previous drive as external USB drive, and copy old Ubuntu data into your fresh Ubuntu.  Then this external device can be wiped (after you are quite sure you have migrated all old Ubuntu data). Or you might wish to keep it in reserve in case you need W10 at some time.

---

### Post by dtree46 on 2019-08-19
> **dragonfly41 said:**
> Brute force idea is to substitute existing drive (containing W10 etc.) with a spare formatted drive and then try to access BIOS.
It might be easier to start afresh with the new drive, install fresh Ubuntu, attach the previous drive as external USB drive, and copy old Ubuntu data into your fresh Ubuntu.  Then this external device can be wiped (after you are quite sure you have migrated all old Ubuntu data). Or you might wish to keep it in reserve in case you need W10 at some time.

OK, help me out please.
My PC is an HP Envy with 32gb ram, 500gb C: with w10, 1tb D: with Linux data. w10 doesn't even see it. E: can't be read by w10, shows but is all red.  F: 250gb external drive that can not be seen and G: a DVD R/W.
If C: is replaced with D:, which is Linux formatted: getting to the BIOS is possible?

---

### Post by dragonfly41 on 2019-08-19
One approach I would try is first create a LiveUSB for your future installation of Ubuntu.  You may already have this.
If not you can create this Live USB on a flash drive in Windows 10 (I believe that Rufus does this, but I have not used my Windows 10 for a long time).
Manually unplug your C: drive (containing Windows 10). Leave your D: drive as it is.
Insert your bootable Live USB and try booting up and getting into BIOS.  But now your previous D: drive becomes C: drive and some reconfiguration is required through LiveUSB operations.

Since you might need Windows 10 for operations such as creating a Live USB I would not wipe this until some time later when you are satisfied that Ubuntu is now stable.  If by chance you have a spare 500 GB drive you might substitute drive C: with this instead of moving D: Ubuntu drive up the tree.  Then with luck you might be able to boot into Ubuntu in drive D:

---

### Post by oldfred on 2019-08-20
If you have UEFI fast boot on (separate setting from Windows fast start up), systems often boot too fast to press any keys.
Normally you can force a normal boot, to give you time to press a key, with a full cold boot, not warm reboot.
Full cold boot is all power off, remove battery if laptop, hold power switch for 10 sec or so to drain and left over power and then restore battery & power on. Immediately press correct keys for your system to get into UEFI settings.

HP usually Escape key & then f9 or f10.
[https://kb.wisc.edu/page.php?id=58779](https://kb.wisc.edu/page.php?id=58779)

---

### Post by dtree46 on 2019-08-20
> **dragonfly41 said:**
> One approach I would try is first create a LiveUSB for your future installation of Ubuntu.  You may already have this.
If not you can create this Live USB on a flash drive in Windows 10 (I believe that Rufus does this, but I have not used my Windows 10 for a long time).
Manually unplug your C: drive (containing Windows 10). Leave your D: drive as it is.
Insert your bootable Live USB and try booting up and getting into BIOS.  But now your previous D: drive becomes C: drive and some reconfiguration is required through LiveUSB operations.

Since you might need Windows 10 for operations such as creating a Live USB I would not wipe this until some time later when you are satisfied that Ubuntu is now stable.  If by chance you have a spare 500 GB drive you might substitute drive C: with this instead of moving D: Ubuntu drive up the tree.  Then with luck you might be able to boot into Ubuntu in drive D:

SUCCESS!!!

Unplugged all drives.
Started Ubuntu Live.
Took a RISK and plugged in former C: while Ubuntu was running.
Installed Ubuntu 18.04 LTS.
It worked.

Thanks to everyone that responded.
Thanks dragonfly41.

---

