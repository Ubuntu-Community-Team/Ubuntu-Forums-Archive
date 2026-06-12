---
title: "Issue with booting Ubuntu 12.04 from external hard drive"
date: 2012-10-21
forum: General Help
---

### Post by HalfFrench on 2012-10-21
I have installed Ubuntu 12.04 on an external hard drive, however to boot it I have to change the "Hard Disk Drives" setting in the BIOS (by putting the external drive above the internal) everytime I restart my computer otherwise it automatically boots windows 7 which is on the internal drive. Upon entering BIOS after shutting down Ubuntu AND unplugging the hard drive this setting seems to reset itself. However if the hard drive is not removed then upon restart the Grub screen comes up. 

Is it possible to make the grub load everytime I start the computer, or an alternative boot screen?

Thanks in advance

---

### Post by oldfred on 2012-10-21
Welcome to the forums.

Is BIOS not retaining the setting to boot external first? Most BIOS save setting but then when not found, go to second setting which then should be the internal drive.  Or are you using the one time boot key (f12 on my system) to just change it for current boot.

Just to confirm system is configured correctly (Will not show BIOS settings though).

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by efflandt on 2012-10-21
For many computers regardless of what you set for boot device order, if you want to boot from a device that is not always connected (or something like CD or DVD), you need to press a hotkey during BIOS splash screen (often F12, sometimes Esc or some other key) to select which device to boot at that time.  That is probably a safety feature so you do not accidentally boot something potentially malicious.  The only virus I ever caught was a boot sector virus spread by floppy disks a long time ago.

If you want grub to always boot whether the external drive is connected or not, grub and a /boot partition (containing /boot/grub) would need to be on your internal hard drive.  Grub can be put in the mbr or on a primary partition (flagged as the boot partition if using Windows mbr), although, it may complain and need to be forced to install the grub boot loader on a partition.  The mbr or beginning of a partition is not big enough for all of grub and its configuration files, which is why it needs /boot/grub whenever it boots, and that would not work if /boot/grub is on the external drive when it is not connected.

There are 2 potential issues having grub in the primary mbr when you have Windows. Some Windows programs may store data in what they think is an unused part of the mbr, but grub2 is somewhat larger than Windows mbr, so they can possibly store data within grub and make it not work (had that issue with Dell DataSafe).  And some Windows service pack updates may refuse to install if Windows is not in control of the mbr (had that issue with a Win7 service pack).

So on sda I actually have grub2 on sda4 which contains 64-bit 12.04.  But I normally boot everything from 11.04's grub in mbr of sdb (which is an SSD containing 64-bit 11.04).  In a pinch, I could either boot sda which with Windows mbr would boot right to Win7, or if I mark sda4 as boot partition, I could boot grub on that partition.

---

### Post by HalfFrench on 2012-10-22
Yeah as you say oldfred I don't think the BIOS is retaining the order for booting in, after unplugging and replugging the external in the order is the internal first despite setting it to boot second. Here is the bootInfo report if that helps: [http://paste.ubuntu.com/1298628/](http://paste.ubuntu.com/1298628/)

As far as I can tell what you are saying, efflandt, ensuring that grub boots before windows is a bit of a hassle. I wouldn't mind pressing a hotkey at BIOS splash everytime I wanted to boot Ubuntu however at the moment I have to go into BIOS, change the boot order and then restart the computer. For some reason F12 doesn't seem to work to give me a one time boot (I have not encountered one time boot before).

Thanks for your help.

---

### Post by oldfred on 2012-10-22
Some systems use other one time boot keys than f12. Does BIOS show the info, many show it just for a second on what key to get to BIOS or what key to one time boot. Or manual for system may have info. 
Usually systems that boot from USB will have the one time boot key also.

---

### Post by HalfFrench on 2012-10-23
Ah yes. F8 does the trick

---

