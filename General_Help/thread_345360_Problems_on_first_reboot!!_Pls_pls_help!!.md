---
title: "Problems on first reboot!! Pls pls help!!"
date: 2007-01-24
forum: General Help
---

### Post by adityak_28 on 2007-01-24
Hi all,
This is almost the 10th time i'm installing Ubuntu so this is getting really frustrating! This is the third different copy of ubuntu 6.10 i'm trying. Ok, I installed ubuntu-desktop on my computer just now. The installation completed successfully. On reboot, the ubuntu logo appeared with the loading bar and after sometime the screen blanked around 5-6 times like it was changing video modes. After that, it provided with 2 pages of errors by the X server. After this the message 

"The X server has been disabled. Restart gdm when it is configured correctly." 

was displayed on the screen. I then pressed Ctrl+Alt+F1 which displayed 

"[17179820.860000] Out of Memory: Kill process 6613 (apport) score 109 and children.
[17179820.860000] Out of Memory: Killed process 6613 (apport)."

and it wouldn't let me log on. I then pressed Ctrl+Alt+F2 and logged in with my username(aditya). On logging, the message

"-bash: /dev/null: Permission denied"

was continuously output on the screen till i intervened it by pressing Ctrl+c. I'm a linux newbie and was looking towards ubuntu to be a good and newbie friendly learning ground. I have tried installing 6.06 (2 different copies) and 6.10 (3 diferent copies). 6.06 used to boot after install only once and would give the same X server error as mentioned above on subsequent boots. 6.10 gives me the above errors. 2 other copies of 6.10 used to give me different errors on each boot so i guessed that my installation media might be bad and downloaded another copy of 6.10. I checked this particular copy by verifying md5 checksum and verified data on cd after burning it (in Nero). This is almost my 10th re-install and the hopes of learning linux seem to be fading by the moment. Does anyone know what should be done now?

NOTE: My system is Amd X2 3600+, Gigabyte GA-M51GM-S2G motherboard (nForce 430. It also has an onboard display which I've disabled through BIOS since I have an external card, 1 GB DDR2 RAM, Seagate SATA II 160 GB HDD, XFX GeForce 7300 GS. I also have WinXP installed on my computer. I do not know if information about my system would help but I provided it anyway...

---

### Post by scrooge_74 on 2007-01-24
try running from command line 

sudo dpkg-reconfigure-xserver  and choose for video driver a vesa driver and a somewhat low resolution.  You may need to get the correct drivers for your video card since it is a Nvidia

Check this site for more info on the video drivers

[http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

---

### Post by adityak_28 on 2007-01-27
ubuntu gives me different errors on every reboot! how is that possible? when i press ctrl+alt+f1 and try logging in at the prompt, it reads my username and password and gives me the login prompt again! i can only boot it in recovery mode but when i typed 'dpkg-reconfigure-xserver' it didn't recognise the command. i tried 'dpkg-reconfigure xserver' and i got the error that the package xserver is not installed.

---

### Post by scrooge_74 on 2007-01-27
sorry my mistake the command is 

sudo dpkg-reconfigure xserver-xorg

---

### Post by adityak_28 on 2007-01-31
i tried simplymepis n opensuse 10.2 yesterday. both the distros installed fine but gave different errors and a lot of segmentation faults during firstboot. as both of these distros installed fine at my friends' places, i figured that the problem was with my computer. i removed the pci express  card and installed ubuntu 6.10. luckily this time, there are no errors  other than the x server error . i'm able to boot to a command prompt. however, i'm unable to sudo anything as i don't know the root password. i tried my username, password and other lame attempts like ubuntu etc. as the root password but it did not work. is there a way i can change the root password?

---

### Post by adityak_28 on 2007-01-31
'sudo dpkg-reconfigure xorg-xserver' does not work. error is 'package not installed'. also gives 'Segmentation Fault: Core dumped'. 

I wonder why no linux distribution boots on my computer. All the live cd's work well but fail at firstboot. I've tried SimplyMEPIS 6.0, Ubuntu 6.06 and 6.10. openSuse 10.2 copies files to computer and reboots to begin post-install procedures however, installation does not resume after reboot and it gives a lot of segmentation fault errors. Is the problem with my computer or is the hardware not supported? I hope some expert can throw some light on this subject.

---

