---
title: "grub conflicting with windows"
date: 2007-02-17
forum: General Help
---

### Post by serious7 on 2007-02-17
ok my uncle bought a new harddrive (160 gig) to put linux and other stuff in. I partitioned it 30/130. I put ubuntu on the 30 and kept the 130 as ntfs. The problem is that i took out my first harddrive(with windows in it) because i didn't want the linux installation to overwrite the important files. Now, i know grub didn't detect windows so i had to refresh the grub in the command line. At one point, i was able to switch between the 2 operating systems by going through the cmos and switching the boot sequence of the harddrives. I went to the command line to fix the grub boot. I did sudo boot. then i did find /boot/grub/stage1. I think it said hd(1,0). But i accidently put setup (hd0). Now i can't boot into the windows partition at all! I tried taking out my second harddrive (with the ubuntu distro in) and leaving the windows hard-drive on but grub keeps coming in and saying it can't boot windows. I want to protect my uncles important files in it. My first priority in this situation is to backup the important files. How can i do that? My uncle has a second computer if i can put the windows hard-drive in that computer.

---

### Post by logos34 on 2007-02-17
Your windows disk *should* be ok, grub just overwrote the bootloader on it but won't boot because there's no entry for windows in menu.lst.  

Do you have a windows install CD? If so, you can restore windows bootloader (NTLDR) by booting frm the cd, going into the REcovery Console and doing the 'fixmbr' procedure.
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by logos34 on 2007-02-17
If you don't have a win install cd, you can use [SuperGrub disk]("http://supergrub.forjamari.linex.org/") to restore the windows bootloader code.

---

### Post by serious7 on 2007-02-17
I want to back up the data first to be sure. Can i put the windows hard-drive into my uncles other computer? WOuld that work?

---

### Post by logos34 on 2007-02-17
> My first priority in this situation is to backup the important files. How can i do that? My uncle has a second computer if i can put the windows hard-drive in that computer.

If the second pc run windows, just plug in the disk, and it will be detected on startup.  You should be able to copy the files without a problem.  It may want to run CHKDSK on it, this is routine so don't panic.

edit: don't change the bios; just let it boot normally to the regular disk.  Then when you get to the desktop you'll see a popup saying 'new hardware detected' or something.  Go to My Computer and you should see an icon there for the drive.

---

### Post by logos34 on 2007-02-17
oh, and if the windows disk is pata/ide rather than sata, make sure to configure the jumpers correctly.  If it was master, and you put it in the slave position in the other pc, change the jumper to slave position.  If the drive in the other pc is in master position but jumpered for 'cable select', you'll have to set the jumper on the drive you're adding also to cable select.

---

### Post by serious7 on 2007-02-17
that's great then. I'll try that once i get to my uncles house. Oh btw, he doesn't know that the computer doesn't work yet cause he's at work lol.

---

### Post by serious7 on 2007-02-17
But for a side question, why doesn't ubuntu access the hard-drive anyways. It gives me an error saying it's not a external disc or something and it says it can't mount it. On my pc, i'm able to access my windows partition on ubuntu. Sorry if this is a simple question because i'm only 15. Maybe that mounting problem is causing the boot issues on my uncle's computer

---

### Post by logos34 on 2007-02-17
Can you still boot into Ubuntu? If so it might actually be easier to mount the windows partition   (it should even though it doesn't boot) in ubuntu and copy the files there or onto the adjacent ntfs partition (but you'll need ntfs-3g driver for that).

---

### Post by logos34 on 2007-02-17
We posted at the same time...

Open a terminal and type these commands, then post output:

> sudo fdisk -l
> cat /boot/grub/menu.lst
> cat /boot/grub/device.map
> cat /etc/fstab

---

### Post by serious7 on 2007-02-17
i'm not at his computer and i don't want to do anything with linux right now (as i am already mad at what happened with grub). I'm still a newbie so i don't wanna risk it. The files in his windows hard-drive is essential for his work. If something goes wrong (ugh), i would get in deep trouble. Can i still access the hard-drive on his other windows machine if it's possible before going through all of this. I want to be 100 percent sure i can back-up the file on a windows operating system.

---

### Post by logos34 on 2007-02-17
> **serious7 said:**
> i'm not at his computer and i don't want to do anything with linux right now (as i am already mad at what happened with grub). I'm still a newbie so i don't wanna risk it. The files in his windows hard-drive is essential for his work. If something goes wrong (ugh), i would get in deep trouble. Can i still access the hard-drive on his other windows machine if it's possible before going through all of this. I want to be 100 percent sure i can back-up the file on a windows operating system.

Well, those commands are just read-only (you can't change the files), but if you don't feel comfortable doing that, that's fine...yes, you should be able to access that hard disk on the other computer as I explained above.

---

