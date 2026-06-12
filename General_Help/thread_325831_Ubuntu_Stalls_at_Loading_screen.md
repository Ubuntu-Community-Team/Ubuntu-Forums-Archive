---
title: "Ubuntu Stalls at Loading screen"
date: 2006-12-26
forum: General Help
---

### Post by CornDog on 2006-12-26
well I have searched this forum for the answer and I am finally reduced to asking a question.
I just finished installing Edgy Eft on my computer. (woohoo) but when I go to start it up it fails at the loading screen. when it gets to the loading screen the little orange bar gets about 1/8 of the way and then nothing happens after that. it just kinda sits there.

Note: I had to use the alternate install CD because the live cd wouldn't boot.

---

### Post by wpshooter on 2006-12-26
How much memory does your computer have ?

Did you check the integrity of your Ubuntu CDs by running the verification function found on the initial Ubuntu boot screen menu ?

Have you ran the memtest function from that same menu ?

---

### Post by maka on 2006-12-26
do you have any external drives connected maybe? if you do, try disconnecting them during bootup and see what happens.

---

### Post by CornDog on 2006-12-26
my computer has 1 Gb of ram, I have checked the cd (it is valid) and I have also run the memory test. I do not have any external drives.

---

### Post by spockrock on 2006-12-26
ok, I am pretty sure this is what it is, what video card do you have? I know newer gpus flat out dont work with the free drivers, so you need to use the proprietary drivers.  So if you can tell me what video card you have I can tell show you a guide to installing your driver.

---

### Post by CornDog on 2006-12-26
my video card is an dual head Nvidia FX 5200 with 256Mb on board memory

---

### Post by spockrock on 2006-12-26
sorry I re-read your post, I thought it froze at gdm, ummm you should be able to boot in verbose mode, by that I mean when you get to grub, highlight the kernel you are going to boot, then press e, then edit the boot line and remove quiet and splash press b and it will boot, showing you what its doing, tell us what happens.

---

### Post by CornDog on 2006-12-26
after removing quiet and splash, I see no difference. how was I to remove them? (I used D )

---

### Post by spockrock on 2006-12-27
> **CornDog said:**
> after removing quiet and splash, I see no difference. how was I to remove them? (I used D )

press e on the kernel you wanna boot, then e on the boot line, then remove quiet and splash, then press b and you should boot and be in verbose mode, I tested this out before I posted so I know it works....

---

### Post by CornDog on 2006-12-27
what am I looking for?

---

### Post by spockrock on 2006-12-28
whats the last thing it does before the crash, or freeze, any error messages

---

### Post by CornDog on 2006-12-29
well the _last_ thing it does before the freeze is the loading bar get about 2 1/2 blocks/bars complete and then it stops. as per error messages it flashes the following right before the loading screen:

[1717957.###000] PCI: cannot allocate resource region 1 of device 0000:01:00.0

(where # == a number that seems to change every time I restart the computer I have seen: 445, 816, 840, in place of the #'s)

---

### Post by spockrock on 2006-12-30
I have no idea what that means, and I am not sure alot of people here will, but the best thing to do is go to launchpad and post a bug or find one similar to yours and see if there is a fix.

---

### Post by CornDog on 2006-12-30
launchpad?
also, do you think I would run into this problem if I installed Dapper?

---

### Post by strabes on 2006-12-30
Hit ctrl + C when it gets to the part that freezes. Also, you could boot into the recovery mode of grub, then do a ```
sudo nano /boot/grub/menu.lst
``` Find the main kernel section; it should look like this: > title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

and remove the words quiet splash. Then save it by hitting ctrl + O then enter, then exit by hitting ctrl + X. Now reboot your computer (just type "reboot") and now try the main kernel boot option. At the very least you'll now be able to see what it is freezing on.

---

### Post by CornDog on 2006-12-31
so I tried installing Dapper and it froze at about the same place. dapper tells you what part is loading at the time and it's stopping on device drivers. I worry that my motherboard is not computable.

---

