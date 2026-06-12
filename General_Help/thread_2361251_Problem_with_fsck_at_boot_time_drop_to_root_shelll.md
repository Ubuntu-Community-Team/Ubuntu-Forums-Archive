---
title: "Problem with fsck at boot time: drop to root shelll"
date: 2017-05-14
forum: General Help
---

### Post by Robbyx on 2017-05-14
Last night I could not get the internet to work using a vpn. Usually I can. I decided to to a fsck -ycfTV  check on my root and home drives.  Home worked. When I run the check on the root drive an error message that the drive was already mounted appeared. After forcing various umount options I had this error message: Can't check if filesystem is mounted due to missing mtab file.  I tried umount /dev/sda2 and was told it did not exist. 

Rebooting and ignoring the advance boot options loads the system.  I have looked at the etc/mstab file and Sda2 is in there. 

What is going wrong?

---

### Post by TheFu on 2017-05-14
**sudo touch /forcefsck** 
then reboot.  That will force the fsck at the next boot.

Mounted file system cannot be checked safely.  You have to boot off alternate media or umount the partition otherwise.  Touching that file is a way to provide your intention for the OS.

---

### Post by Robbyx on 2017-05-14
I tried your advice but it has not improved my situation because  I can not run fsck on sda2 which is where my root is stored. I usually run the program from the root shell in repair mode but it will not run because it claims the drive is mounted. This does not make sense because we are not at the stage in the boot where the partitions are mounted.  Strangely if continue with the reboot Ubuntu loads without any error! I would have expected an in use error

---

### Post by TheFu on 2017-05-15
Perhaps I wasn't clear.
```
sudo touch /forcefsck
sudo reboot

```
That's it.  You don't get to run the fsck. The system does it at boot, automatically. No manual steps after those 2.

---

### Post by Robbyx on 2017-05-15
Thank you for your help. Do you know how to stop the /forcefsck?

I followed your command line and rebooted, but it would always stop and drop me into the emergency mode. I could not reach the login stage. There was a short report advising that error: unable to locate ioapic for GSI  56.

I have been able to get into my machine by updating the grub in recovery mode. It lets me in provided the graphics is not good ie the first time in after the update.

I have just change the default grub_cmd.... default  line and added in noacpi and have run the grub update command. I would like to cancel the forcefsck command, because I fear it will never complete the check. I suspect the forcefsck is a one off command, but it has to reach the end of the check to be canceled. I am going to try a reboot and hope....

Hope not realised. I could not boot in without the fsck command running and then stopping before the end. It was throwing me into a grub emergency repair screen.

I am making it worse. I have just changed the etc/default/grub line to 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off noapic nolapic nomodeset"

Now, the computer shows  a blank screen with nothing happening. I hit esc and nothing showed. I fear it had crashed the computer. I have to do a hard boot.

---

### Post by Robbyx on 2017-05-15
This is from my fstab (sda is the boot drive and it is a SSD)

# swap was on /dev/sda1 
UUID=82ec0704-5c1e-4b9d-bdcf-4c5fb10cb548 none            swap    sw              0       0

# / was on /dev/sda2 
UUID=692268a0-db31-4874-bcba-077ec47a2dad /       ext4   defaults,discard,errors=remount-ro  0 0

---

### Post by Robbyx on 2017-05-15
I can't even use the grub emergency repair because I type in dvorak and it is not set up at that point!

---

### Post by TheFu on 2017-05-15
If the file system is so corrupted that fsck doesn't work, you have bigger issues.  Do you have another HDD?  If not, I'd get one ASAP.  Corruption is usually the last level of issues before a HDD dies.

To stop the automatic running of the fsck, remove the file from the root directory. Usually it is easiest to boot from alternate media to do that.  While you are in there, might as well manually try the fsck on the unmounted partition/LV.

I hope you have some backups.

---

### Post by Robbyx on 2017-05-15
I ran the liveCD and was able to use fsck on sda2 with no problems. I think what is happening is there is a flag that indicates if a partition is in use. I do not know where it is or if it exists but that fits the original problem with the partition being mounted, when it was not mounted at that point.

fsck does work on the forced start but stops when it comes to the ioapic error.

---

### Post by TheFu on 2017-05-15
It is a 'dirty' flag for the file system on Linux system.  That will cause the system to replay the journal and continue. It usually takes 1-2 seconds and all is fine.

Some more ideas - bad cable?  Failing sata port?

/forcefsck has been around and used for 25+ yrs. It is part of file system design to solve a specific issue.

I'm guessing you've googled the specific error and seen some of the same things I'm seeing.  Didn't see a real solution anywhere.

---

