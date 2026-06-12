---
title: "Help Please Grub Ubuntu 16.04"
date: 2017-08-28
forum: General Help
---

### Post by tomg- on 2017-08-28
Hello, I recently installed Windows 10, Ubuntu and Kali Triple Boot 
But i have ran into one issue trying to customise grub, i wanted to install Grub customizer but grub has the kali splash screen now,
i installed kali after Ubuntu i cannot find a way to get the customizer to work on kali and i would overall prefer to have Ubuntu as the owner/os  in control of the grub
so if i edit the file on grub on Ubuntu it works but that does not appear to be the case after installing kali 

Sorry if i put this in the wrong place also sorry if i have made a dumb mistake in assuming how it works, in reality i am really dumb and get confused easily
This is my first time using this forum
Thank You

~Ty/tom

---

### Post by westie457 on 2017-08-28
Hello tomg- welcome to Ubuntu Forums.
The quick way to get the 'Ubuntu Grub' to take control is boot into Ubuntu open a terminal type in and run this command. sudo update-grub
You might have to do this after a kernel update to kali.

---

### Post by tomg- on 2017-08-28
I have tried that and it made no difference i think...
what do you mean Kernel Update?? i have heard of it but i'm not familiar with it 
99% of my knowledge is random >~<
Gonna try it again just incase

Edit:
Tried sudo update-grub and still nothing changed
im gonna try Grub customizer and see if it alters it in any way

---

### Post by oldfred on 2017-08-28
Are all systems installed in same boot mode, or all UEFI or all BIOS?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I prefer manually customizing, but you then have to learn a bit about grub2. Grub customizer adds its own grub files & backs up grubs files. But sometimes that can add issues.

       
 [http://askubuntu.com/questions/848119/how-to-update-grub-on-a-dual-boot-machine/848614#848614](http://askubuntu.com/questions/848119/how-to-update-grub-on-a-dual-boot-machine/848614#848614)
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by tomg- on 2017-08-28
Okay i managed to do it 
I went to Grub Customiser and went File > Install to MBR (Master Boot record) and after it installed successfully it is now working
Thank you very much  for helping me

---

