---
title: "Tried Installing Ubuntu 13.04 with Win8, didn't work, lost partition, HELP!"
date: 2013-09-24
forum: General Help
---

### Post by Jackylegssss on 2013-09-24
So, I tried installing Ubuntu 13.04 alongside Windows 8. I created a 50GB partition beforehand. I had the install disk. I was going through setup, and I got to the part about where to install to. Naturally, I pick the partition I made. I set the file format system to EXT4 Journaling File System (or something like that), and the directory as '/'. These were the ones I saw used in a tutorial on Youtube. I went through the rest of the set up fine, and after it was done installing it said it needed to reboot, so I clicked 'reboot now' in the window. A text thing popped up saying that it was waiting for all programs to close. It was just white text on a black background. It stayed like that for about ten minutes with no change, so I just hit the reboot button on the case. It rebooted, but went strait to loading Win8, without the option to load Ubuntu. Frustrated, I reboot, go into the BIOS, and try to manually select, but there is no option there. I could choose to boot the HDD, which would go strait to Win8, or from my DVD-RW drive, which was empty. I load up Win8, check under 'My Computer', and notice that the partition is gone, and the normal drive is 50GB smaller than previous. I have no idea how to get back that space, or how to get Ubuntu to work (I think I screwed it up). Any advice?

---

### Post by oldfred on 2013-09-24
Welcome to the forums.

Windows does not correctly see ext4 partitions. So from Windows not seeing the Linux partition or seeing it as unformatted is normal.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

