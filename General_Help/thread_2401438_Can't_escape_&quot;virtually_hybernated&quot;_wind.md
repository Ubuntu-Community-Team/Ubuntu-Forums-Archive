---
title: "Can't escape &quot;virtually hybernated&quot; windows!"
date: 2018-09-18
forum: General Help
---

### Post by khodd on 2018-09-18
I bought a cheap chinese netbook, a Teclast F7, with win 10 pre-installed on a 64BG eMMC. Installed ubuntu on 16GB partition, while waiting on 128GB M.2 2242 SSD. Don't often boot into windows but did a few weeks ago. It did an update without asking and without me noticing, then battery went flat or I shut it down, anyway windows installation corrupted and video card playing up very badly. Wont allow me to do a factory reset. And here's the thing, Win 10 uses "virtual hibernation" to reduce boot times and this bypasses bios (or uefi) during boot. So I can't install ubuntu on my new SSD as I can't escape the windows environment. Any type of reboot takes me back to where I was in windows, including disconnecting the battery for a full day. Attempt to change uefi setting from within windows failed. Can't remove eMMC as it's soldered in. Tried to nuke windows partition using gparted etc but nothing will touch it as it is mounted. Every other tool I have looked at seems to have the same limitation. I am now perplexed and annoyed. 
Anyone have any ideas? I'm happy to lose windows. Have even thought about trying to un-solder the eMMC (if I could figure out which chip it is) but I think that's just the alcohol talking.
Ta, RH

---

### Post by Autodave on 2018-09-18
You need to get into the BIOS.  Have you tried CTRL + ALT + DELETE to get to a shut down menu?  If you can get that far, you can try F7 to get into the BIOS.  You need to start smacking that key rapidly as soon as you power it on.  Another option (if that doesn't work) if you can get it to power down, is to attach an external keyboard and quickly and repeatedly press the F2 key on power up.

---

### Post by westie457 on 2018-09-18
Plug in your Ubuntu install USB before starting this.
At the Windows log on screen click the power icon for a shut down/restart menu. Hold the Left Shift button and click restart (if you get a warning about other users being logged on and losing info in open docs click Restart Anyway while holding the Left Shift button).
You should be taken to the Windows Recovery options screen. Select Troubleshoot then select Advanced then Use a UEFI/USB Device. Your USB stick should show in the menu. Choose that and Reboot.

---

### Post by khodd on 2018-09-18
This just gets weirder and weirder. External keyboard worked, but bios wouldn't see any of my usb drives. Then managed to get bootable ubuntu usb to boot from one of the windows restore options. Installed ubuntu and told it to use entire disk, which it did, although there are possibly a few very small volumes left from windows. 63 of 64 gb is now a linux partition. So ubuntu boots, but the video problem is still there. Hardware problem? Maybe, but the thing the video has done since the windows update is to show ghostly layers of previous screens (some much more persistent than others). And now that I'm in ubuntu it still shows these ghostly screens from windows! It doesn't look or act like physical screen burn (surely impossible anyway? Sharp IPS panel, "imprint" instantaneous), but how could the graphics system remember what was there after multiple reboots? Have disconnected the battery, again. Rebooted, but windows artifacts still there. Very strange, and I'm beginning to think it's terminal. Any idea what might be going on?
Cheers,
RH

---

### Post by khodd on 2018-09-19
Also now that I've installed ubuntu I can't get into the bios again! Just wondering, is there any linux tool that would allow me to completely format the eMMC in case something there is still getting in the way of accessing the bios? I've got an SSD ready to plug in but no way of installing ubuntu on it. Having a drive soldered down is very annoying!

---

### Post by westie457 on 2018-09-19
If you are still able to get to the UEFI settings pages look for the reset to defaults. Hopefully this will clear the 'nvram' and possibly reset the graphics, I have no idea if this will work. If it does work you can then manually reset the options you want.

To get a 'Grub' menu when booting tap the Esc key immediately after power on. The last line should read 'System Setup', that is your BIOS/UEFI pages.

Now for the dangerous part; wiping the internal drive. Do this from your Ubuntu USB in 'Try' mode.

Open a terminal run 'sudo fdisk -l' to find the correct drive. It might be listed as '/dev/sda' or '.dev/nvme0'.
Also in the terminal check the man page for 'gdisk' for ideas on how to wipe the drive and give it a new partition table.

This next part can go wrong.
Or in the terminal carefully type 'sudo dd if=0 of=/dev/nvme0' #or what fdisk showed for  the internal drive.
When that has finished open 'Gparted' > click the 'Device' menu > Create Partition Table' > GPT > Apply.
Click the Install icon.

If after all of this you still have problems reinstall Windows and send the thing back for a refund. Buy something different.

Windows 10 can be downloaded for free from Microsoft and provided it is being installed to a previously activated machine no licence number is needed.

---

### Post by khodd on 2018-09-21
Many thanks for the above input. Tried a bunch of the stuff above, and did some more research, and am leaning toward it being a faulty video card. Will try sending it back but it came from Hong Kong so that might be tricky.

---

