---
title: "double boot requires restart"
date: 2013-07-30
forum: General Help
---

### Post by onlineaddy on 2013-07-30
Hello,
I have Ubuntu 12.04 and Windows 7 installed. The default in the boot manager is Ubuntu. Whenever I want to switch to Windows the boot manager doesn't let me select it (W7 is at the bottom of the list and the selection is stuck at Ubuntu). Only when I do the reboot by pressing the off button on the PC the selection can be moved to start Windows. Now, when I do that and I reboot to go back to using Ubuntu, the selection is on Ubuntu but doesn't automatically boot Ubuntu. I need to press Enter to load the system. 

It didn't use to be like that. Could anyone provide a solution? It's really annoying to have to reboot in order to change the OS.

---

### Post by oldfred on 2013-07-30
Are you using a USB keyboard. And then have you changed your settings in BIOS to include the USB keyboard & mouse. I had similar issues, both Windows & Ubuntu seem to use their own drivers but as grub is loading it uses some sort of default from BIOS. My keyboard and mouse worked from the old PS/2 ports in grub, but once I changed the settings in BIOS everything worked.

Grub is also sensing you forced a shutdown. After a crash it does not auto boot and want to you decide if you want to use recovery or not. Once correctly booting you should be ok.

Also best not to force shutdown. But I am not sure at grub menu if this works, only once booted into Ubuntu.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by dcstar on 2013-07-31
> **onlineaddy said:**
> Hello,
I have Ubuntu 12.04 and Windows 7 installed. The default in the boot manager is Ubuntu. Whenever I want to switch to Windows the boot manager doesn't let me select it (W7 is at the bottom of the list and the selection is stuck at Ubuntu). Only when I do the reboot by pressing the off button on the PC the selection can be moved to start Windows. Now, when I do that and I reboot to go back to using Ubuntu, the selection is on Ubuntu but doesn't automatically boot Ubuntu. I need to press Enter to load the system. 

It didn't use to be like that. Could anyone provide a solution? **It's really annoying to have to reboot in order to change the OS**.

You always **must reboot** a running system to change what OS you are running. Shutting down the PC and restarting is not "rebooting", it is powering off and powering on.

---

### Post by VMC on 2013-07-31
> **onlineaddy said:**
> ...
It didn't use to be like that. Could anyone provide a solution? It's really annoying to have to reboot in order to change the OS.
Sounds like you want a [virtual machine]("http://en.wikipedia.org/wiki/Virtual_machine") ,where you can boot concurrent OS's.

---

### Post by onlineaddy on 2013-07-31
> **dcstar said:**
> You always **must reboot** a running system to change what OS you are running. Shutting down the PC and restarting is not "rebooting", it is powering off and powering on.

It doesn't matter if I reboot or power off and power on - the result is the same. If the last system I was on was Linux, then at GRUB I cannot move the selection down to highlight Windows and if I don't do anything Linux is loaded by default. So if I want Windows, I need to shutdown the computer at GRUB and power on again to make the selection. If the last system was Windows, then at GRUB I need to manually hit ENTER for Linux to start loading. 

@oldfred:
Thanks! I will try what you suggested on my PC (it's not a laptop). I will also check BIOS for any settings. My keyboard is not USB, it's got a PS/2 cable connector.

---

### Post by onlineaddy on 2013-08-15
> **oldfred said:**
> Are you using a USB keyboard. And then have you changed your settings in BIOS to include the USB keyboard & mouse.

OK, I have checked everything as you suggested. I'm using a PS/2 keyboard so I didn't change anything in BIOS. I did a double check of BIOS to see anything suspicious, but couldn't find anything. 

> **oldfred said:**
> 
Grub is also sensing you forced a shutdown. After a crash it does not auto boot and want to you decide if you want to use recovery or not. Once correctly booting you should be ok.

Correct. It does boot OK after a successful boot. The problem is whenever I want to change the OS from Linux to Windows and vice versa. 

Any other solutions that I could try? Thank you.

---

### Post by oldfred on 2013-08-15
It should not be, but maybe the ps/2 keyboard. I have not had one of those for years. And they usually worked when the then new USB keyboards did not work.

I do not know what the error is and that is what should be corrected.

Some work arounds would be to create a script or manually edit grub.cfg (which we say to never edit) to change the default boot. Or install grub to a flash drive to use to boot Ubuntu and have the Windows boot loader on the MBR of the hard drive.

---

### Post by onlineaddy on 2013-08-16
Thank you, oldfred. I suppose it will be much easier for me to just do a fresh install to get rid of the problem. I have an LTS 12.04 so it will be a couple of years before I do so. In the mean time, if anyone has any idea how I could check the error in the terminal, or anywhere else, please let me know.

---

### Post by VMC on 2013-08-16
Try running bootinfoscript(see my blue link), so we can see if any problems are in your boot files. copy/paste RESULTS.txt

---

