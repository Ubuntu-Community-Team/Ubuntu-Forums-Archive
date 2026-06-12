---
title: "Trouble with SSD and Installation"
date: 2013-06-05
forum: General Help
---

### Post by pfhunk on 2013-06-05
This past weekend I decided to install Ubuntu onto my 128GB SSD. I booted into the liveCD, after wondering/researching what kind of partition scheme would work best (I also have a 1TB HDD).  I realized I was a little over my head (trying to install Linux next to my Windows7). I chose the default partition settings and let the installer begin. During the partitioning, it threw an error. I go to boot back into Windows and get stuck on my Asus motherboard screen (press delete to enter UEFI BIOS settings). It also would not boot to the liveCD anymore. I unplugged my SSD, which allows me to get to my BIOS settings as well as boot into the liveCD. When I plug it back in after booting, however, it is not recognized by the filesystem or gparted (also tried sudo fdisk -l).  I recently downloaded knoppix to investigate further but I have to go to work for now. 

I understand I may have messed up my SSD, I just hope I didn't kill it. It would be great to salvage some data from it, but if not, oh well. I just want to be able to reformat it and reinstall Windows as well as Ubuntu (correctly).

Thanks for reading. Any suggestions?

---

### Post by oldfred on 2013-06-07
If you can boot Ubuntu with hard drive plugged in run this so we can see details, may not fully work with Knoppix:

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by pfhunk on 2013-06-07
When I try to boot with the SSD plugged in (to either SATA port) it does not even make it to the POST screen... If it's not read by the BIOS, I've been told by Samsung I can do an RMA.

---

