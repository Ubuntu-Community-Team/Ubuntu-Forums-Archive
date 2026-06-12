---
title: "messed up partitions HELP!!"
date: 2007-10-13
forum: General Help
---

### Post by Gdobbs on 2007-10-13
In installed ubuntu, but in trying to get my resolution to work right I made it so it would only load ubuntu in text. I re-loaded the CD of ubuntu, and deleted the partition that ubuntu was on. hoping I could just re-install it. I restarted my computer, and it says something about an error in the boot manager, and I cant load windows. fortunatly I can still load ubuntu from the disk. if I install ubuntu back onto the partition (now unallocated space) it was on before will it re-allow me to load windows? Thanks.

---

### Post by taurus on 2007-10-13
Yes, reinstalling Ubuntu will recover GRUB.   Otherwise, boot from Windows CD and remove GRUB from MBR if you want it to boot Windows.

---

### Post by Martin Witte on 2007-10-13
as long as your windows partition is not touched you should be able to create a partition with a filesystem in the empty space, and reinstall ubuntu here, when grub gets installed it should find the windows partition

---

### Post by Gdobbs on 2007-10-13
Worked like a charm, Thanks! by the way, I messed it all up once, is there a sure fire way to fix resolotuions? or is the next version of ubuntu planning on fixing it somehow and I should just wait?

ps. Synchmaster 920nw (1440x900 is the best resolution)

---

### Post by Happy_Man on 2007-10-13
Well, Gutsy is working on improving its monitor-resolution finding abilities, but a surefire way to do it now is to open a terminal (Applications --> Accessories --> Terminal) and enter the command ```
sudo dpkg-reconfigure xserver-xorg
``` Follow the onscreen prompts, generally just keep hitting enter until you get to a screen with a long list of monitor resolutions. Scroll to your selections, press spacebar to select, and then hit enter to keep going when you finish choosing. Keep hitting enter until the wizard exits, and then reboot. Hopefully, you should be able to change your resolution to something better now. :D

---

### Post by vanadium on 2007-10-13
In addition to the comment above, I suggest you check that xresprobe is installed. Thus, first install xresprobe using synaptic, then run the command above. I learned on a Dutch forum that xresprobe is not present in a standard Ubuntu install (Edgy, Feisty). This causes dpkg-reconfigure xserver-xorg not to work properly in detecting your video properties.

---

### Post by Gdobbs on 2007-10-13
When I run that command, and follow the instructions (hitting enter) It comes to this, and stops:


Users of PowerPC machines, and users of any computer with multiple video  &#8593;  
 &#9474; devices, should specify the BusID of the video card in an accepted        &#9646;  
 &#9474; bus-specific format.                                                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Examples:                                                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;  ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For users of multi-head setups, this option will configure only one of    &#9618;  
 &#9474; the heads.  Further configuration will have to be done manually in the X  &#9618;  
 &#9474; server configuration file, /etc/X11/xorg.conf.

---

