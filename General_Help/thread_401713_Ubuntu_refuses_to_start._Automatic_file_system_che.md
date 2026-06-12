---
title: "Ubuntu refuses to start. Automatic file system check failed. Manually required."
date: 2007-04-04
forum: General Help
---

### Post by PureRumble on 2007-04-04
I was using my computer and I installed a program with Synaptic. When the installation had been completed, the bar at the bottom and the top of the screen just freeze and refuse to respond. I shut down by pressing the power button on the tower quickly so the Quit-windows shows up. Then I choose restart. But it simply refuses to do anything. So now I hold the powerbutton down 5 secs to force a shutdown.

When I start up and choose the Ubuntu-partition, the start-up screen shows up (the one with the bar). When it reaches about 20% it freezes, and then the following text is presented to me


* Checking root file system...
/etc/rcS.d/S20checkroot.sh:407 logsave:not found

* An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed in maintenance mode with the root filesystem mounted in read-only mode 


The story goes on. It then tries to start up some commands that obviously fail. I am then presented with a prompt. Running fsck will do no good. It simply states that there is no such command.

I am now running from the liveCD. I managed to run sudo fsck on /dev/hda3 and it fixed something (last time of writing was in th future), and then stated that it was "clean". But this still won't help me out. I am presented with the same problem when I reboot and startup my Ubuntu-partition.

My HD layout

/dev/hda1 FAT32 (compaq-recovery partition)
/dev/hda2 NTFS (my windows XP partition)
/dev/hda3 EXT3 (my linux partition)
/dev/hda4 SWAP (the swap partition)

How can I solve this?

---

