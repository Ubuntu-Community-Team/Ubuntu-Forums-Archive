---
title: "MediaSmart EX470 - Getting random shut downs after installing Ubuntu"
date: 2014-04-15
forum: General Help
---

### Post by randypfau on 2014-04-15
I have an old HP Mediasmart EX470 which is headless, I pulled out a drive and put it into another computer and installed ubuntu. I got the drive all ready to go and went back to the mediasmart server and put it in with no other drives in the bays. The system appeared to be booting, so I connected to SSH via putty from another machine. Then out of nowhere it shuts down.

Is there anyway I can use SSh to troubleshoot these issues? I dont know if Im overheating the mobo/cpu/power supply, the hard drive, or if there is some hardware/bios or issue that is shutting down the machine.

The strange thing is, that the server worked fine before I started this project and when it was running Windows Home Server and never had any of these symptoms.

---

### Post by scott45 on 2014-05-09
Hey randypfau

I just upgraded my EX470 to [SIZE=1][/SIZE][h=2][COLOR=#000000][SIZE=1]Ubuntu Server 14.04 LTS[/SIZE][/COLOR][/h]I had a hell of time getting my EX 470 to run so I ended up purchasing a vid/mouse/keyboard cable from [http://www.mediasmartserver.net/forums/viewtopic.php?f=6&t=8066](http://www.mediasmartserver.net/forums/viewtopic.php?f=6&t=8066) made all the difference. I had set up my EX470 same as you. After I installed the breakout cable I was able to see what was happening in the BIOS and boot I found that the SMI partition / SSD on the motherboard was trying to boot the recovery mode for WHSv1. I ran the UBUNTU server set up and made sure the GRUB loader was on the 2nd drive (this is the normal WHSv1 boot drive). 

Also In Bios set:
 Advanced BIOS Features / Hard Disk Booting Priority / 2nd drive (this is the normal WHSv1 boot drive)
Advanced BIOS Features / Integrated Peripherals / SIS OnChip PCI Device / SIS Serial ATA Mode [4P(IDE)+4S(IDE)]
 
After that on boot the machine always goes to Ubuntu server and recognized the other 3 drives I added.

So you really need a breakout cable to get it done hope this helps.

---

