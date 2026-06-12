---
title: "Ubuntu crashes on boot - help needed"
date: 2007-11-16
forum: General Help
---

### Post by jseligma on 2007-11-16
Ubuntu crashes on boot. GRUB loads and the ubuntu load bar gets about a quarter of the way across before switching to a black screen and then rebooting. I've tried exiting from quiet mode but the there isn't much text before the reboot, and it goes by fast. I don't think there was an error message.

I have a dual-boot system with Windows XP, Ubunu 7.10, and a separate data partition (ext3) on which /home is installed. Everything worked fine until Windows crashed. I booted from a Live CD and tried to access my data partition to transfer data to an external drive. As soon as I clicked on the drive, the system crashed again. I booted in Windows, but there was another crash, and so I booted from the Live CD again. This time the Windows partition and my external drive had been corrupted. Ubuntu prompted me to run a command to properly dismount the drives (something with "mount" and "-force" - I forge the details), This worked and I was able to mount both drives and transfer the data from Windows to my external drive. But when I tried to access the data partition, the system crashed again. 

Is my only option now to reinstall both Windows and Ubuntu? If so, is there any way of recovering data from my data partition?  Fortunately, most of my data is on the external drive but still, I would prefer to look over the data partition, if possible. And what is the likely cause of all this?  I've run checks on my hard drives and they seem to be okay. I'm guessing that my faulty Windows installation caused the initial crash and that the hard reboot messed up my drive and corrupted part of my Ubuntu installation. But maybe I should be thinking of other hardware causes, such as the power supply. 

Comments and/or advice appreciated.

---

### Post by K.Mandla on 2007-11-16
You should be able to use any live CD to get your data off the drive. I would suspect that when Windows crashed it left a nasty trail in its wake, and somehow that's preventing Ubuntu from starting up.

You might try booting the machine to the Grub menu, then editing the kernel line and taking out "splash" and "quiet". You'll get a mess of terminal messages as it starts up again, but this time you should be able to see what's causing the reboot.

---

### Post by jseligma on 2007-11-16
Thanks for the reply. 

I also thought that I "should" be able to recover data using the Live CD, but I don't know how to. Trying to mount the data partition (/dev/sda4)  by clicking on its icon under places>computer causes a crash and reboot.  Is there a more indirect way of getting at my data?  

Thanks for the tip about editing the kernel line in GRUB to remove "quiet" and "splash". That enabled me to see a little more than just hitting Alt-F2, which is what I did previously. The reboot occurs while the system is "Checking file system" and finds an "exception". My /home is on the data partition which causes the problem mentioned above, I guess that it is getting stuck when trying to mount that drive partition. 

One idea is to tell ubuntu to look for /home on another partition. Would I have to reinstall ubuntu to do that?  And if I did, would there be some way of getting at the data on the data partition?

---

### Post by jseligma on 2007-11-19
In case anyone is interested, I didn't find a solution to this problem and so I bought a new drive and reinstalled everything, losing my data in the process. Fortunately, almost all of it was backed up. The best guess is that either my corrupt Windows installation messed up the drive or the drive messed up Windows and my Ubuntu data partition. In any case, the lesson I learned from this is not to try to install a second OS as a way of coping with serious problems with the first OS, at least not on the same drive.

---

