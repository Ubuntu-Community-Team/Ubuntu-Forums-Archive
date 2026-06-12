---
title: "Stall during boot / GPIO conflict"
date: 2015-10-23
forum: General Help
---

### Post by pierre-lonchampt-4 on 2015-10-23
Dear all.

I have an asus eeeBox which I have been using for a while as a media/filesserver - used headless in my basement - with two USB drives to host my files (one main one backup), a Samba server to serve the general files and miniDLNA for the media bits. I woudl remote (rdp) to it for configuration etc.
For that I had installed xubuntu (15.04 by memory) on a second partition, keeping it up to date, while leaving the "native" Ubuntu 12.04 as it was as a recovery option. 

Yesterday I tried setting up a webcam (logitech quickcam) on it to setup some Haloween special effects fro my kids.
I plugged the webcam in, then installed cheese. The webcam was recognized nicely in dmesg.
But when starting cheese I had some Xorg error messages which I didn;t study in much detail - I though this was due to Rdp not working as expected.

So I went back to my basement with screen, KB and mouse to try to sort it out directly - and hell began.

After shutting down to unplug the USB HDs  (not enough avail otherwise to plug KB and Mouse) and rebooting...the machine would stall on boot. The boot message would appear showing the boot choice, then just a underscore prompt then black screen and the display woudl go to sleep.
I've tried VGA and DVI. no difference.
I've tried choosing to boot from the latest kernel or earlier ones . no difference.

I've tried booting in recovery mode from each kernel: it gives a short "dmesg type" message before crashing...but still crashing.
The fans are turning after that, the LED is ON, but I cannot remote to it either, and I cannot ping it; my router doesn't see it either (I have configured it on fixed IP in the router).

When booting from the recovery 12.04 and mounting the second  partition, there are no recent log files that I can find in var/log.

I've tried starting without the kb and mouse - no difference.

Attached are the video of the log message before the crash (only way I could capture it!!)[ATTACH=CONFIG]265133[/ATTACH]

Any help clue appreciated. 
I've tried that (by modifying the grub file from the 12.04 boot, with no change.
[http://unix.stackexchange.com/questions/97974/how-do-i-remove-acpi-warning-on-boot](http://unix.stackexchange.com/questions/97974/how-do-i-remove-acpi-warning-on-boot)

THX a lot

---

### Post by pierre-lonchampt-4 on 2015-10-28
Still banging my head.

This thing (eePC 103x, can't remember what x is ) also refuses to boot from USB/SD card.
I have verified my booting media (xubuntu 15.10 i-386), it boots just fine on two other machines.

On this one, I have
a/ most of the times just a prompt (underscore) on black screen, then monitor goes to sleep
b/ sometimes the keyboard / HID icon at the bottom of the screen, then monitor goes to sleep
c/ Once I have had the xubuntu splash screen, , then monitor goes to sleep

Is the machine dying/dead?

I just don't understand why the existing "default" install (12.04) boots all the time with no problem.

I don;t think it is the bootloader (grub 2.somethign beta) as the live media does not boot either... 

Should I try to flash/repair the bios?

---

