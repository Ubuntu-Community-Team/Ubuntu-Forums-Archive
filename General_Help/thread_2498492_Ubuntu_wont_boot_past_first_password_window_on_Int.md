---
title: "Ubuntu wont boot past first password window on Intel NUC 10"
date: 2024-06-16
forum: General Help
---

### Post by huggatit on 2024-06-16
I have used a single boot Ubuntu on a NUC 10 without a problem for 3 years.

It started freezing recently possibly due to memory or partition being full.

Today it froze and when i try to reboot i can only enter the first password then the system freezes.

usually i enter two consecutive passwords to get it to boot.

I have a backup recovery file on USB stick , what is the best way to get this to do a recovery without reinstalling Ubuntu ?

Is there a way i can boot in safe mode and do a scan for hardware faults before doing a full recovery and possibly losing files ?

thankyou

---

### Post by tea for one on 2024-06-16
> **huggatit said:**
> It started freezing recently possibly due to memory or partition being full.
Can you boot into a "Try Ubuntu" live session, open a terminal and enter:-
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```
Please post the output within code tags for legibility
> Today it froze and when i try to reboot i can only enter the first password then the system freezes.
usually i enter two consecutive passwords to get it to boot.
One password must be login, what is the purpose of the second password?
> I have a backup recovery file on USB stick , what is the best way to get this to do a recovery without reinstalling Ubuntu ?
Is this a personal data backup?
Or full image (e.g.Clonezilla or similar)?
> Is there a way i can boot in safe mode and do a scan for hardware faults before doing a full recovery and possibly losing files ?
There are various choices via grub and advanced options.
Can you reach the grub menu?

---

### Post by huggatit on 2024-06-16
The backup file was created with Ubuntu > Utilities > create backup , however once i got into BIOS and changed the boot order to USB , That backup will not run.

re passwords , i dont remember exactly why but it has always required 2 passwords , once at the Ubuntu splash screen , then it asks for a second password to open the OS.

i tried the "lsblk -e etc etc but it didnt open anything , just reverted to a frozen page .

i tried to use Rescatux to do a boot rescue but couldnt create a bootable USB with Etcher or RUFUS , just wouldnt work for me.

I at least have most of my precious files on a seperate HDD so i didnt lose too much off my OS system drive , i think i will just try a 3 year old bootable USB with Ubuntu 20.0 that i used and just do a fresh install

thanks for your thoughts.

---

### Post by currentshaft on 2024-06-16
At the grub selection screen (right after BIOS POST), press E to edit the currently selected kernel, use your arrow keys to replace navigate to the line that being with "linux" and ends with "quiet" and append "init=/bin/sh", something like this:

linux ... ro quiet init=/bin/sh

Then press Control-X to boot. This will (hopefully) drop you into single-user "safe" boot where you can execute commands and see what's wrong.

---

### Post by deadflowr on 2024-06-16
> however once i got into BIOS and changed the boot order to USB , That backup will not run.
?
The default backups aren't a recovery tool that can be booted.
It's just a simple tool to backup your personal files to be restored onto a clean system.
(or to revert changes you may have made to files on a working system).

You'd need to reinstall the operating system and then restore your backups.

If you want a system recovery backup utility there are plenty out there.

>  I tried the "lsblk -e etc etc but it didn't open anything , just reverted to a frozen page .
It doesn't open anything, it should have outputted a listing of devices and possible mounted locations and file system types, etc.

---

### Post by tea for one on 2024-06-16
> **huggatit said:**
>  i think i will just try a 3 year old bootable USB with Ubuntu 20.0 that i used and just do a fresh install
Why not consider a more recent LTS version - Ubuntu 22.04 or 24.04?

---

### Post by huggatit on 2024-06-17
Update ......

after unsuccessfully trying to restore my backup while running Ubuntu from a bootable USB I next reinstalled my entire version 20.04  and found the backup file would then restore successfully.

however after reading posts above it wouldn’t hurt to update to v24.04 ?

If I download 24.04 from another computer and do a fresh install will I be able to restore my v20.04 backup on to the newer v24.04 ?

thankyou

---

### Post by tea for one on 2024-06-17
> **huggatit said:**
> If I download 24.04 from another computer and do a fresh install will I be able to restore my v20.04 backup on to the newer v24.04 ?
Yes - perfectly acceptable strategy.
Restorable backups are everybody's safety net.

---

