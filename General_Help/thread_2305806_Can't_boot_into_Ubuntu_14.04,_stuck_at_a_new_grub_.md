---
title: "Can't boot into Ubuntu 14.04, stuck at a new grub screen"
date: 2015-12-09
forum: General Help
---

### Post by White_Wind on 2015-12-09
Hi everyone, here is my situation.
On a HDD partition I run Ubuntu Mate 14.04.3 64bit and on a 2-SSD volume I run Windows 8.1 64bit. When I need to boot in the other OS  what I do is I head to the UEFI and change the boot order and restart, I didn't set up the grub to choose from there instead (maybe will do later).

Okay, so I was uninstalling adobe flash player from my ubuntu, I was deleting some remaining files manually when I accidentally deleted the /lib64 folder and restarted my machine.
Boot was impossible, there were error messages and the Caps Lock and Scroll Lock lights of my keyboard were blinking, and I was stuck there.

I hard reset, went to the UEFI to change the first boot option to Windows and booted into it. I created a Ubuntu Mate 14.04.2 64bit bootable flash drive, using UUI.
I restarted my machine, went back into the UEFI to set the usb drive as the first boot. But there were 2 entries for the usb drive: the usb drive alone and the usb drive marked as [UEFI] (saw that one later).
I chose the entry not marked as [UEFI] and I landed on a grey and green grub screen that I had never seen before, with 3 entries: "Ubuntu", "Advanced Ubuntu Options" and "System Set Up". The third entry leads to my machine restarting straight into the UEFI, and trying to boot from the 2 other options led me to be stuck with blinking keyboard lights again but no error messages.
I don't even know if that grey and green grub screen is the one of the ubuntu inside the flash drive or the one of my main ubuntu.

I hard reset, back in the UEFI, selected the usb drive option marked as [UEFI] as first boot this time, and I got a black and white grub screen from which I've been able to boot into the flash drive.
From there, I mounted and accessed the partition of my main ubuntu, reinstated the /lib64 folder and recreated in it the symlink it used to hold. So now I would think that in the partition everything got back to what it should be.

But I tried to restart my machine and it got stuck at the starting screen, just before one can enter the UEFI (so at that moment, the option for the first drive to boot was still set on the flash drive).
I hard reset, tried F2 again and same thing, still stuck there. I removed the usb drive and now booting into the UEFI is possible. I select my main ubuntu as the first boot, I restart and there I land on the grey and green grub screen, the one that I had when trying to boot into the flash drive unsuccessfully, and when trying to boot all becomes stuck again, still with the flashing keyboard lights.
If I insert back the flash drive and restart, the machine gets stuck at the starting screen.

Do you think it is still the partition that is faulty or is it the grub? I don't know what to do, I prefer to ask you before I mess things for good.

And [here is what I followed]("http://ubuntuforums.org/showthread.php?t=2163328") when trying to solve my problem in the first place, that case is the same as mine (but in Ubuntu 13.04). But I didn't copy/paste the /lib64 folder and the symlink in it from the usb drive like the guy did, I copy/pasted it and its symlink, tried to create the symlink with the command line (it failed, the file was already in it), I deleted the symlink and finally created it successfully.

---

### Post by White_Wind on 2015-12-10
The symlink I created was pointing to a non-existing file. I guess that symlink doesn't point to the same file in Ubuntu 13.04 and in 14.04.
I just copied/pasted the /lib64 folder and the symlink it contains from my live usb to my main ubuntu partition, and that did it. I'm relieved :) I can access my OS and I don't get the grey and green grub screen anymore.

Silly me in the first place, that'll teach me to be even more careful.
Now I will look into what programs I can use to diagnose if anything got unhealthy in my system. I will look around but if you know what may be good for that, well I'm listening.

---

