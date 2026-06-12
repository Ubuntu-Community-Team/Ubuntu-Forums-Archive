---
title: "Disk error press any key to restart."
date: 2007-05-07
forum: General Help
---

### Post by Penguinw on 2007-05-07
I am not sure what has happened. I have installed xp after ubuntu, but i have not got the usual error, something like grub error 17, all i get this time is Disk error press any key to restart.

The only thing i have done different is that i have grub installed onto a different hard disk.

If you need any information about my computer please ask.

also i have tried this "https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows" that usually works.

-Philip

---

### Post by dirtmcgirt75 on 2007-05-08
Same error here.

HP nx6110 laptop which already has Windows XP loaded.  Tried booting from Ubuntu 7.04 CD (second copy from a second source).  Boots to main splash page, select install Ubuntu.

Get the following error:

booting from local disk, 
disk error 01, 
boot failed

Something about my hardward that doesn't jive with 7.04 perhaps?

---

### Post by Penguinw on 2007-05-08
What i have done is installed ubuntu again on another portion. this has worked but when i select windows xp in grub it says the disk error, or boot error i cant remember.

---

### Post by ckhung on 2007-07-18
Same here.  Mine is an ASUS R2H UMPC. 
I used to have a few copies of mandriva 2006,
edubuntu 6.10, and edubuntu 7.04 installed in
separate partitions, and I used grub from mandriva
to boot. Yesterday I tried to install Windows XP in
a primary partition. Instead of grabbing hold of the
MBR as usual (after which you can fix by re-installing
grub using the mandriva CD in "linux rescue" mode),
this time the Windows installer died by itself when
trying to reboot, spitting out the same message
    disk error
    press any key to restart
Using the recovery CD of R2H I was able to install
windows. Then I fixed the MBR the usual way by
re-installing grub from Mandriva. Now other partitions
boot ok but when I choose to boot windows, it gives
the same error. It seems that this is not ubuntu specific.
I suspect it has something to do with specific hardware
since this setup of mine has been replicated in several
desktops and a few laptops without problem.

---

### Post by &#1581;&#1587;&#1606; &#1573;&#1576;&#1585;&#1575;&#1607;&#1610;&#1605; on 2007-09-29
has this been solved or not?
because I have the same problem...
installed xp after ubuntu feisty
instead of writing it's boot loader.. xp messed up
with "disk error.. press any key to restart"
tried recovery console for "fixboot" , "fixmbr" ... nothing fixed that...
then reinstalled grub from ubuntu live-cd and everything is just fine as it was, the hard disk is ok and all partitions are fine.
then again tried the windows boot loader.. "disk error"
so.. any suggestions ????

---

### Post by &#1581;&#1587;&#1606; &#1573;&#1576;&#1585;&#1575;&#1607;&#1610;&#1605; on 2007-10-01
for those interested
within the winxp setup.. formatting the partition as NTFS solved the problem for me

---

### Post by melenor on 2007-12-28
formatting did not help me i have also tried vista still getting "disk error prss any key to restart" now i have actually reformated dirve and tried installing XP/Vista first and i still get this error. Any help? thanks.

---

### Post by indiecast on 2008-04-19
i seem to be having this same problem. im going to try the NTFS thing. anyone have a specific answer?

anyone?

anyone?

buler?

---

### Post by jesusfreak107 on 2008-04-19
uh... wow.  a lot of people seem to be having the same problem!  try going into your BIOS, and rearanging your boot order, people.  installing Ubuntu on another HDD makes it the primary boot drive, but if your computer is set to boot off of the other one, you would have a problem.  as far as accessing your BIOS goes, it differs from computer to computer.  you have to press a certain key, generaly one of the F1-12 keys, but mine requires the delete key, so it depends on the machine.

---

### Post by indiecast on 2008-04-19
it seems to be fixed

i got to the second part of the install


i had it formated fat32 from gparted

i reformated it with NTFS from the win2000 installer and right before starting it i put the CD above the floppy drive in my boot order

i think the solution was the NTFS install tho, because it has worked before. but if NTFSifying it doesnt work try your boot order.

im running one hdd and installed 7.10 first

and yes, i do realize i will have to reinstall grub, but ive got that set and im confident this will all work this time

thanks,

indiecast

---

