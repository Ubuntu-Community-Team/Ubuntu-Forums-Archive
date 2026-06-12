---
title: "Help! System won't boot after RAID 5 install"
date: 2007-02-22
forum: General Help
---

### Post by caffienda on 2007-02-22
I set up a 5 disk RAID 5 array using mdadm.  I had problems after trying to mount it with etc/fstab (the computer went to a root login to fix the issue) I got frustrated enough I decided to wipe my HD's and re-install.  

I ran DBAN on my 5 IDE drives in the RAID setup and AUTOKILL on my 36GB Raptor.  I got 75% the way through the wipes and re-booted.  

I re-installed 6.10 server and now I am getting a blinking cursor in the upper left hand corner.  
I tried re-installing 3x now!  I've tried the boot priority in the BIOS and everything. 

Any Ideas?

I get the following when I boot after a TOTAL power off:
> 
Boot Failure
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot Device
Press any key when ready

I just tried the "rescue" option on the Server CD and I am getting this on the reboot after re-installing GRUB:
[quote]Error 5: Partition table invalid or currupt

press any key to continue...{/quote]

---

### Post by Yoooder on 2007-02-22
Are you trying to run your root partition within your RAID array?  If so, this is generally a bad idea, as you have found out if the raid array has problems you will have a terrible time getting things fixed.

If not you can try removing the raid array from your fstab, or setting it to not automatically mount.  Then you can get into your system and use mdadm to see the status of things.  Try doing a 'cat /proc/mdstat' to see the status of your arrays.  It should list something if it's seeing them.  When I setup my array I had issues with it basically losing it when I would reboot.  I can't remember the specific remedy, but one thing I did was to allow it to complete it's initial rebuild before rebooting.

---

### Post by caffienda on 2007-02-22
> **Yoooder said:**
> Are you trying to run your root partition within your RAID array?  If so, this is generally a bad idea, as you have found out if the raid array has problems you will have a terrible time getting things fixed.

If not you can try removing the raid array from your fstab, or setting it to not automatically mount.  Then you can get into your system and use mdadm to see the status of things.  Try doing a 'cat /proc/mdstat' to see the status of your arrays.  It should list something if it's seeing them.  When I setup my array I had issues with it basically losing it when I would reboot.  I can't remember the specific remedy, but one thing I did was to allow it to complete it's initial rebuild before rebooting.

No I installed the OS to a 36GB Raptor (which had 3 partitions, sda1, sda2, sda5; /, swap, extended).

I removed the array from fstab and it allowed me boot regularly w/o having to login as "root" to fix the fstab error.

I then did "sudo mdadm -remove /dev/md0" and "sudo mdadm -remove /dev/md1".  This seemed to remove the array.  I then did a fdisk for all the partitions and deleted them all and closed fdisk with "w" to write the changes to the drive.  
       I also tried the "rescue" selection from the install CD, I tried to fix grub and I actually got a system prompt (which I think was the root prompt from the install CD) and this allowed me to view the partition info with fdisk.  I deleted all partitions and wrote the changes.  

I don't care about anything on any of these drives at this point.  I just want to get my OS drive (SATA Raptor) back up and running.  Can there be a corrupt area on any of these drives after creating a RAID array?

---

### Post by caffienda on 2007-02-22
I'm trying to use KILLDISK (which is on the Ultimate Boot Disc; UBC) to wipe the disk to all zeros.  This should reset any partitions, correct?  Or do I need to do something else for that.  I'd just like to set the drives back to factory default and start over.  

I just loaded my Ubuntu 6.10 DVD and booted the Live version.
my "cat /proc/partitions" resulted in this:
> 8   0   36151920  sda
8   1   34652173  sda1
8   2               1  sda2
7   0      647432  loop0

 and ran "sudo fdisk /dev/sda"  I am getting this warning when the screen comes up:
> Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

command (m for help):

I then deleted the deleted the 2 partitions and wrote the changes, entered back into fdisk /dev/sda,  entered "p" to see the partitions and there were none.

This should be a clean disk, right?

Thanks!

---

### Post by caffienda on 2007-02-22
I think it might be working.?.  Even though the system was supposed to boot to the ONLY HD, it didn't.

---

