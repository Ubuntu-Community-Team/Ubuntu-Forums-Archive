---
title: "Please help with my Ubuntu induced BIOS troubles"
date: 2021-05-11
forum: General Help
---

### Post by totalviking on 2021-05-11
Hello, I am very new here, but I'm at my wit's end.

I recently bought a 2-in-1 ASUS laptop. Naturally, it came preinstalled with Windows 10 Home edition, which I don't want.

The background:
I tried out a couple of different Linux versions using the live USB demo mode that most Linux distros have. Eventually, I settled on Ubuntu 21 because of it's out of the box support for touch screens and coming with a WiFi driver (which is helpful as the laptop neither has an ethernet port nor a standard sized USB port). 

The prelude:
After installing Ubuntu 21 I ran into a pretty consistent total system freeze (about an hour to two hours after boot). I looked up help and found that all of the system override/interrupt keys didn't work. It would only respond to holding down the power button.

Obviously, this is less than usable. During my attempts to fix it (allocating more swap space and trying different combinations of applications running) I found I could no longer access `sudo apt-get <command>` commands. The terminal asked me to run `dpkg --configure -a` which I tried, and it said I needed to set a secure boot password. So I did.

Current problem:
As I have been unable to fix the freezing issue that lead me down this merry chase. I've decided to install either Linux Mint 20.1 or Fedora Workstation over my Ubuntu OS. The problem is that I can no longer select my boot device when in the BIOS, whenever I attempt to disable secure boot, it reenables secure boot the moment the power cycles. This was not a problem before I installed Ubuntu.

Current advice I could find online is to send the laptop back to the manufacturer as I "do not have full control over my computer". However, I know I had before. Alternative advice I've found was to delete the platform key in the secure boot menu, but other Web forums say that this will mean that I can't boot into anything at all if I do so.

I'm at a loss, and I really would like a working laptop, but I've tried everything and gotten less than what I started with. I would really appreciate some help, even if it's only just a, "Have you tried this."

---

### Post by totalviking on 2021-05-11
Apologies, I meant to type platform key, not package key.

---

### Post by TheFu on 2021-05-11
This isn't enough detailed information for anyone to help.  Details needed. Lots of details.  What have other people using the exact same hardware found working related to Linux?  Bleeding edge can be very painful. That's the best case situation, if there aren't any hardware faults.

I'd say put Win10 back on it and return the device ASAP.  Then get a different device which is actually known to be compatible with the version of Linux you'd like to run.

There will always be issues with this device if you have having the sorts of problem described. Can't tell if it is Linux or the hardware.

Is the exact model a state secret?  Can you run and post the detailed output from **inxi -Fxxxxz** so we can see an overview?

---

### Post by totalviking on 2021-05-11
Sorry, I probably should have thought to include the model. The Laptop is an ASUS VivoBook Flip 14 TP401MA. I bought it from Argos as it was the only retailer in the UK to stock that model of laptop. 

I haven't been able to find any information regarding people using Linux on the exact same model of laptop as I am. 

Hardware Specs include:
14" 1920x1080 LED Touchscreen 
Intel Pentium Silver N5030 1.1GHz processor 
Intel UHD 605 Graphics
4GB 2300MHz RAM
128GB eMMc storage drive

It has a UEFI BIOS.

I cannot put Windows 10 back on it. In part because the manufacturer didn't include a Windows boot/restore drive, but also as I currently am not able to change the boot order.

If there are any other details that I've neglected to mention, please let me know.

---

### Post by TheFu on 2021-05-11
Run the requested command, please.
Post the output.

The world needs stubborn people to make stuff like this work by hunting down every driver, for every chip inside the system. If nobody else has already got this working, you are in a world of unknowns.  Hardware like that can be very difficult.  I would take it back just to avoid the hassles, but that's me. I've only been using and administrator for systems 25+ yrs.

---

### Post by oldfred on 2021-05-11
Even with 4GB of RAM which should be enough for Ubuntu, a lighter weigh flavor would be better for a lightweight system like this.
I have an old laptop with only 1.5GB of RAM, could not get recent full Ubuntu to install. Older versions would install, but be so slow as to be unusable as always using swap. I then used fallback/flashback as lighter weight GUI, similar to old before Unity Ubuntu.
I installed Kubuntu which is not really a lightweight flavor & it worked reasonable well.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

Have you updated UEFI?
You may need to change UEFI settings. Either full cold reboot, not warm reboot,  or some of these light systems have a pin hole on back to reset system. Also last menu item in grub menu, is a way into UEFI settings. Just press down arrow as booting as long as you did not change grub to 0 seconds delay on boot. Or from inside Ubuntu.
Reboot into UEFI:
sudo systemctl reboot --firmware or
sudo systemctl reboot --firmware-setup

May be similar models:
Asus Vivobook 15 Intel i5-8250 CPU
[https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane)
Asus Vivobook S14 S430FN 18.04 - Intel firmware update required
[https://ubuntuforums.org/showthread.php?t=2424764](https://ubuntuforums.org/showthread.php?t=2424764)
Asus Vivobook S15
[https://ubuntuforums.org/showthread.php?t=2375408](https://ubuntuforums.org/showthread.php?t=2375408)
ASUS VivoMini UN45 UEFI update required to see NVMe drive
[https://ubuntuforums.org/showthread.php?t=2355295](https://ubuntuforums.org/showthread.php?t=2355295)
[https://ubuntuforums.org/showthread.php?t=2402972](https://ubuntuforums.org/showthread.php?t=2402972)

If you want a better system, and have a USB port, add an external SSD to boot from.

---

### Post by tea for one on 2021-05-11
> **totalviking said:**
> Current problem:
As I have been unable to fix the freezing issue that lead me down this merry chase. I've decided to install either Linux Mint 20.1 or Fedora Workstation over my Ubuntu OS. The problem is that I can no longer select my boot device when in the BIOS, whenever I attempt to disable secure boot, it reenables secure boot the moment the power cycles. This was not a problem before I installed Ubuntu.

Secure boot is part of the UEFI specification and it is not controlled by Ubuntu.

Anyway, can you not access the UEFI set-up pages and re-set to factory defaults?
Once re-set to defaults, then:-

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM

Can you boot your USB device?

---

### Post by totalviking on 2021-05-11
When I attempt the command you suggested (inxi -Fxxxxz) I get
`Command 'inxi' not found, but can be installed with: sudo apt install inxi`
I also tried to prefix the command with sudo and got
`sudo: inxi: command not found`

Furthermore, as I booted it just now, I no longer have WiFi. So I'll only be able to copy out the information from the terminal via the old Mk1 eyeball.

---

### Post by totalviking on 2021-05-11
Well thank you all for your assistance, but when starting the laptop to attempt to the reboot UEFI from Ubuntu, Ubuntu's interface began to flicker - a lot. This problem continued on all successive boots. At this point all of the commands suggested in this thread have been met with the terminal failing to recognise the command. 

I've cleaned the laptop, and placed it back in it's [s]grave[/s] box with the intention to return it to the retailer.

Thank you for your rapid responses, but I'm finally happy to chalk this one up to faulty hardware. I've spent a week and £380 on this laptop. I think it's time to cut my losses.

---

