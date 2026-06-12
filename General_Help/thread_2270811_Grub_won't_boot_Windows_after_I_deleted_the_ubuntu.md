---
title: "Grub won't boot Windows after I deleted the ubuntu partition"
date: 2015-03-25
forum: General Help
---

### Post by Cincinnatux on 2015-03-25
I have a Dell XPS 9530 that I originally configured to dual boot Windows 8.1 and Ubuntu. I've been too busy to actually play with the Ubuntu partition and it has been a year since I last booted into it. I decided it was time to delete the Ubuntu partition and extend mg Windows partition to occupy the whole drive. It turns out that was more problematic than I had figured.

I cannot get my laptop to boot now.

It starts up a Grub terminal with minimal bash support.  How do I fix this?  

I am in the final month of grad school and really need to be able to finish this thing in Windows. I can delete everything after graduation, but the size of the files I'm using demand that I let Windows hog the hard drive for now.

---

### Post by anaconda on 2015-03-25
Well..
When you deleted your Ubuntu-partition, you also deleted part of your boot loader (grub) So now your grub wont work any longer.

You could re-install ubuntu with a separate /boot partition which could be eg. 200MB in size...
And then you could delete your bigger ubuntu partition and you would still have a working grub-bootloader. (the 200MB partition) and you could still boot to windows...

re-installing ubuntu does re-install grub-bootloader and it will detect your windows so you can boot to windows. 

Or you could jus boot with a windows install DVD and select the "repair boot" -option (or similar. you can google it)

---

### Post by anaconda on 2015-03-25
Here is a link about restoring windows bootloader
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by oldfred on 2015-03-25
If your install was UEFI based, you should just be able to go into UEFI and choose Windows as new default.
All Windows 8 systems pre-installed are UEFI boot.

---

### Post by Cincinnatux on 2015-03-25
Thanks for the great info!  The short-term solution I'm using is oldfred's suggestion:  I went into UEFI and the option to boot Windows was right there.  Problem solved.  I'm backing up all my data right now, then I plan on following anaconda's advice to restore the Windows bootloader.  

Before reading oldfred's suggestion, however, I had tried to boot from a Pendrive Linux thumb drive (with 14.04 LTS) but my UEFI must be set not to boot from USB, and it dumped me at the Grub prompt instead.  It is intimidating how few commands are recognized by that Grub prompt....  I think tomorrow I'll work on booting the Pendrive Linux dongle just to make sure I can still do that.  It would suck if UEFI prevents USB booting.....

Anyhow, thanks to both of you for taking time out of your day to help a fellow Penguinista.  I'll return to Ubuntu as soon as I can shed myself of the University's reliance on Windows!

---

### Post by oldfred on 2015-03-25
Some systems in UEFI mode require you to enable USB ports. And some of those require you to set a password to be able to change some settings. Never lose that password if required.

I build new system with Asus AR motherboard and it had many settings that had to be changed and be correct to get it to boot flash drive in UEFI mode.

---

