---
title: "No INIT Found"
date: 2013-01-19
forum: General Help
---

### Post by neilbfromshus on 2013-01-19
I have just purchased a laptop with ubuntu 12.04 LTS on it. i am not very familar with ubunto. never used it before. i locked myself out of the administrator account and didnt know the password. i then had to shutdown the machine in a guest account. when i came to restart the computer it came up with the No INIT found try passing to bootarg. I have tried to load from a livecd created from unetbootin on a usb stick (4gb) (windows based selection)and i have switched boot device to boot from usb. but it does nothing i just get a blank black screen. can anyone help me please.

---

### Post by Bashing-om on 2013-01-19
neilbfromshus; Hi Welcome to the forum.

Give this a try and see if it gets you back up.

As you have a USB live media, set in bios to boot from the usb device.
Boot the install, when the purple splash screen appears (bottom has "stick"figure and keyboard emblems) hit any key ->language screen->escape key to accept the default language ->boot option screen -> choose "boot from first hard drive":
hit the shift key -> grub menu -> arrow down to "recovery" kernel: enter
Recovery menu -> choose fsck.

fsck is ubuntu's file system check/repair, when fsck completes -> choose resume normal boot//will be in a degraded graphical state, that is OK. Let the system boot up to the desk top and then reboot.

All look good now ? If so will advise you on how to reset your password in your next thread.[INDENT][INDENT]just try'n to help 
[/INDENT][/INDENT]

---

### Post by neilbfromshus on 2013-01-20
Hi Bashing-om,
Thank you for you reply. I have tried a few times to boot from Bios set to usb and all i get is the black screen with a cursor in the top left hand corner. no prompts or messages or anything. The usb does flash though as it it being read. I have even tried to boot my operational PC from Bios usb to see if the stick is readable. no joy. I have been told that livecd on usb is not very effectively downloaded and that i may need to create the stick 6 ot 7 times. I have even done this with no difference. the main message I seem to be getting out of running recovery mode is that the device cannot see the directory with my OS on. Fdisk -l does not work in the grub shell screen that i am in (i cannot get into the ubuntu terminal) but when i run blkid it advises that I have TYPE="ext4" on sda1 and on sda5 I have TYPE="swap". there is no mention of sda2/3/4.

I am not sure what to try now. Hope you have some further ideas I can try.

---

### Post by Bashing-om on 2013-01-20
neilbfromshus;

Let's "assume" that your usb has a good copy on it, and the problem is that  a graphics driver is not loaded, inducing the black screen.

Try this: Boot up the usb install, soon as the bios splash screen clears depress and hold the shift key-> ubuntu boot options screen -> f6 key ->choose "nomodeset" option ->f10 key to continue the boot process.

Can you now boot to the GUI ?
[INDENT]one step at a time, gets there !
[/INDENT]

---

### Post by circa on 2013-01-20
It sounds as if your usb stick wasn't formatted prior to using Unetbootin, as Unetbootin doesn't do this for you. You should have at least got a boot menu, which would allow you to select Ubuntu installation.

---

