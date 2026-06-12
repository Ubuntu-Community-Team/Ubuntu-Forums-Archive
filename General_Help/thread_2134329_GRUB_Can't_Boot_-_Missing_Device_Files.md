---
title: "GRUB Can't Boot - Missing Device Files"
date: 2013-04-10
forum: General Help
---

### Post by conte_matthew on 2013-04-10
Iwas installing a software library using apt-get and all of a sudden I  see it tampering with my /boot directory. I canceled the installation  but somehow it deleted all the sda device files from the /dev directory.  When I try to boot now, all of my OSs are listed but when I selected  Ubuntu, I get an error saying that it cannot find the device and I  should try to boot manually. I can't do that though because the device  files are gone.  I've followed the advice from these questions:

  [http://ubuntuforums.org/showthread.php?t=1769391](http://ubuntuforums.org/showthread.php?t=1769391)
  [Boot error > no such device: grub rescue]("http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue")

  But I think my situation is different. My partitions are intact; I  was able to mount my Ubuntu partition while running the Live CD and all  the data is there. How can I restore the device files?

-- Extra Info --
  Here's the output from BootInfo script:
  
============================= Boot Info Summary: ===============================   
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      for (,msdos6)/boot/grub on this drive.  

sda1: __________________________________________________________________________ 
     File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows Vista     Boot files:        /bootmgr /boot/bcd /Windows/System32/winload.exe

  sda2: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:        /bootmgr 

 sda3: __________________________________________________________________________      File system:       Extended Partition     Boot sector type:  Unknown     Boot sector info:   

sda5: __________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:

   sda6: __________________________________________________________________________      File system:       ext3     Boot sector type:  -     Boot sector info:      Operating System:  Ubuntu 11.10     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img   

I also tried to run grub-install on the mounted partition as suggested by one of the posts I linked to but I got this error
  
ubuntu@ubuntu:~/tmp$ sudo grub-install --root-directory=/home/ubuntu/tmp /dev/sda6 /usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea.. 
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
 /usr/sbin/grub-setup: error: will not proceed with blocklists.

---

### Post by oldfred on 2013-04-11
Your link is to a Mac with gpt partitioned drives. That is a lot different than most PCs.

Better to post full BootInfo. But post link not entire output.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by conte_matthew on 2013-04-11
Here is the output from Boot-Repair:

[http://paste.ubuntu.com/5698675/](http://paste.ubuntu.com/5698675/)

---

### Post by conte_matthew on 2013-04-11
I managed to repair grub using Boot-Repair. Now I can actually boot into  Ubuntu but I get a black screen before the login and can't do anything.  The first time, it did the disk check before going to a blank screen.  (No terminal prompt, just completely blank.) Is there a way I can at  least get a terminal to try to figure out what's wrong?

---

### Post by conte_matthew on 2013-04-11
I managed to repair grub using Boot-Repair. Now I can actually boot into  Ubuntu but I get a black screen before the login and can't do anything.  The first time, it did the disk check before going to a blank screen.  (No terminal prompt, just completely blank.) Is there a way I can at  least get a terminal to try to figure out what's wrong?

---

### Post by oldfred on 2013-04-11
In the grub submenu does the recovery mode work. It includes a nomodeset.
Or you can edit grub menu with e, and on linux line replace quiet splash with nomodeset.

---

### Post by N3XU5 on 2013-04-11
Why would you cancel it? Cancelling something when it's 50% done usually makes things worse. Especially when it is your /boot directory.

---

### Post by oldfred on 2013-04-11
Thread closed.
Duplicate
[http://ubuntuforums.org/showthread.php?t=2134346](http://ubuntuforums.org/showthread.php?t=2134346)

Please do not create duplicate threads. We are all volunteers here and need to not duplicate info in another thread.

---

