---
title: "bad file system or hardware failing - help please?"
date: 2007-09-24
forum: General Help
---

### Post by sjhupp on 2007-09-24
Hi all, firstly thanks to all those who contribute to these forums - have got me a long way thus far.
But now I actually need to post myself, so hoping someone could please help me before I lose my HDD ... again.  I have an Ubuntu box with the following specs:
- Athlon XP 2800+
- GA-VM400AM board
- 1 x 80Gb Seagate IDE HDD
- 1 x 160Gb Seagate SATA HDD
- Ubuntu 7.04 up to date, running mythtv (frontend & backend)
- Twinhan DTV card, Leadtek DTV1000 card, 1 Gb ram, 17" LCD, kb & mouse etc...

I have, just in the past month or so, started having issues with what I assume is the file system. 
I originally had Ubuntu on the 80Gb IDE drive (ext3), and the 160gb as the recording drive for mythtv (XFS). I started to hear sounds emitted from the 80Gb drive: 
<drive spins up> ... "tick" .. "tick" .. 
<drive spins up> ... "tick" .. "tick" .. 
So spins up and ticks twice, then repeats once more.  System freezes whilst doing it, and can happen when just using firefox, nothing intensive.
Also got some random, albiet not frequent crashes with blank screen.
Fsck revealed many I/O file system errors, which I fixed, then it happened again. Created error in mythtv recordseek table too. 
The file system errors were around an I/O file system or read/write error on hda. I cannot exactly remember now, as I can no longer boot the PC with the drive plugged in (hangs at grub), so don't know how to access the data on it! :(  suggestions?

Anyway, thinking it could be the drive, I unplugged it & re-formatted the 160Gb with ext3 partition for Ubuntu 7.04 & mythtv again, then XFS partition again for mythtv to use.  Again I get the same sounds from the drive, crashes, and error lines similar to sCSI I/O read error. Have googled and seen people have got the same message for usb drives in Ubuntu, but this is not usb, nor SCSI, but SATA.
Could anyone suggest what I can check please? I don't wish to use the PC any more without further instruction, for fear of losing this HDD also. Happy to boot up & run some specific commands tonight to provide further info to help.

I'm not sure if it's a problem with mobo/chipset support, BIOS settings (HDDs are auto, LBA), XFS or what, so any help greatly appreciated. My mythtv setup is so close to finished! ...

---

