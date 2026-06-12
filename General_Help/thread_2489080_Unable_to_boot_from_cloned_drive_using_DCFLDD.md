---
title: "Unable to boot from cloned drive using DCFLDD"
date: 2023-07-18
forum: General Help
---

### Post by danik56 on 2023-07-18
Original system drive is 1TB NVME M.2 SSD. Running Ubuntu 22.04.
created an image file using DCFLDD running off a Live USB on said system.
Moved the image file to another system, and restored it successfully to a 1TB external 2.5 SSD drive.
Using Gparted i verified the partitions appear identical and was able to access the data.
When I attemped to reboot from the cloned drive, at first the Ubuntu logo showed up for a while, then
a black screen appeared, displaying:

You are in emergency mode. After logging in, type "journalctl -xb" to view system logs, "systemctl reboot" to reboot.

What is the problem here, and how do I login to view the system logs and figure out the cause of the problem?

---

### Post by oldfred on 2023-07-18
Full installs to external drives boot from /EFI/Boot/bootx64.efi using name or label of drive in UEFI boot entry, just like the live installer. Full install also requires the /EFI/ubuntu/ for parts of boot.

External drives on same system as used to install, may not have an ESP - efi system partition and boot from UEFI entry "ubuntu" in internals's drive eSP like an internal drive. 

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by danik56 on 2023-07-18
OK. will report back with the requested info.
Btw, I also tried to take out the original M2 SSD from the first system, and attched it as external USB drive (using adapter) to the 2ed system, 
and was able to boot just fine.

---

### Post by danik56 on 2023-07-18
Question on using Boot-Repair.
If running off Live CD, how do you tell the utility which boot drive to report on ?

---

### Post by tea for one on 2023-07-18
> **danik56 said:**
> Question on using Boot-Repair.
If running off Live CD, how do you tell the utility which boot drive to report on ?
You reported that the cloned drive does not boot, therefore only the cloned drive should be attached.
Then, boot-repair will automatically provide the report for the non-booting device.

---

### Post by danik56 on 2023-07-18
The cloned drive is attached in addition to an internal HDD.  so should the internal HDD be removed ?

---

### Post by oldfred on 2023-07-18
You need report to show everything.

---

### Post by danik56 on 2023-07-19
Report uploaded as URL:      [https://paste.ubuntu.com/p/h2tGBqqQvZ/](https://paste.ubuntu.com/p/h2tGBqqQvZ/)

The cloned device is /dev/sdb

---

### Post by tea for one on 2023-07-19
Thank you for posting the boot-repair report.

sdb is not an exact clone of sda e.g.

```
NAME   FSTYPE     UUID                                 PARTUUID                             LABEL  PARTLABEL
sda                                                                                                
&#9500;&#9472;sda1 vfat       7528-6085                            9ef3e83a-38c1-4f61-8f7f-0dcded8ad3ef        EFI System Partition
&#9492;&#9472;sda2 ext4       03675b6f-34a6-4225-b3a6-bb67320e1371 71413197-f609-4960-a54b-18c5d5183d19        
sdb                                                                                                
&#9500;&#9472;sdb1                                                 f5ab10ac-54ff-4cd0-bafc-b721e04599c2        EFI
&#9500;&#9472;sdb2 vfat       512A-5348                            bbd2a0da-cfe0-49f9-89e3-a120aa22e8b1        
&#9500;&#9472;sdb3 ext4       d60db62f-b21c-4874-8f6f-16d1a8dbf265 ca6d63eb-15e9-4b25-ae7a-ee7ac835956d        
&#9492;&#9472;sdb4 zfs_member 5131516330742586901                  4cdd268c-ba91-4f34-9f26-e73d15adf9df zpool1 SSD_ZPOOL
```

Do you still want to create a clone of sda?

---

### Post by danik56 on 2023-07-19
sda is not related to the cloned device. sda is where I booted from so I can run Boot-Repair.
sdb is the cloned device which I am unable to boot from, and i get into emergency mode.
I have also uploaded the journalctl output from the failed boot attempt:

pastebin.com/A7YF1cMh

---

### Post by yancek on 2023-07-19
The link in your last post is not valid.  In post 7, oldfred suggested you show everything which means you should have both the cloned drive and the original attached.

The boot repair output shows you have Ubuntu 16.10 installed in EFI mode on sdb3 and sdb4 is the cloned partition.  You should not expect the cloned drive to boot when you have both drives, the original drive and the cloned drive attached.  You also show an ntfs partition on the cloned drive which you had not mentioned previously.

I would suggest you attach the original drive and run boot repair again and indicate which drive is the drive cloned and which is the cloned drive.

I'm not familiar with zfs so I don't know what differences there are between in an a normal install/boot.

---

### Post by danik56 on 2023-07-19
I have the journalctl output in a text file.  How do I upload it here so it can be viewed?

It is stored in my dropbox here:  [https://www.dropbox.com/scl/fi/1agnovmnuj3v3x6q76pko/journal_log.txt?rlkey=uq6nfua6y0nazimbsi576ag00&dl=0](https://www.dropbox.com/scl/fi/1agnovmnuj3v3x6q76pko/journal_log.txt?rlkey=uq6nfua6y0nazimbsi576ag00&dl=0)

If I attach the original drive as /dev/sdb in addition to the drive in /dev/sda, I can boot from /dev/sdb just fine.
only when the cloned drive is at /dev/sdb in addition to the drive in /dev/sda then I get the problem.
Btw, I don't see any NTFS partition on /dev/sdb.

---

### Post by oldfred on 2023-07-19
You cannot reboot with a cloned drive.
Duplicate UUIDs are not allowed.

You have labeled sdb1 as ESP, but are using sdb2. Incorrect label will not make any difference, but no need for two FAT32 partitions unless you want it for some other reason. 

Install in sdb3 is 16.10 or long expired. It will not update.
And boot loader in ESP for sdb

Line 243 shows ESP is trying to boot from an UUID that does not exist.
You need to reinstall grub and use ESP in sdb2. You have to use Boot-Repair's advanced mode to choose an install & choose a drive like sdb, not sdb2.

---

### Post by danik56 on 2023-07-19
"[COLOR=#000000]You cannot reboot with a cloned drive.[/COLOR]
[COLOR=#000000]Duplicate UUIDs are not allowed."

[/COLOR]The original drive is not connected to the machine.  /dev/sda is a different drive with 22.04 that I used to boot so I can run Boot-Repair.
The /dev/sdb drive is the cloned drive. when I boot from /dev/sdb I get the Grub screen showing both 22.04 and 16.10 excatly as it comes up when booting from the original drive on the original machine.
The error occurs after I select 22.04 on the Grub screen and hit ENTER.

when booting from the cloned drive and getting the emergency mode prompt, I issued "blkid" and verified that the UUIDs match what is specified in "/etc/fstab"

The cloned drive and the original drive appear identical in GPARTED.  Both have 4 identical partitions.

I should note, that original drive is NVME M.2 SSD, and the clone drive is 2.5 SSD (not M.2).   don't know if this has anything to do with the problem. 


[COLOR=#000000]


[/COLOR]

---

### Post by danik56 on 2023-07-20
From looking at the journalctl output its clear the OS started to come up:

     Jul 19 10:05:47 ZITO-UBUNTU kernel: Linux version 5.15.0-71-generic (buildd@lcy02-amd64-044) (gcc (Ubuntu 11.3.0-1ubuntu1~22.04.1) 

About 2 min later, this was the last message before the emergency mode prompt was displayed:

     Jul 19 10:07:23 ZITO-UBUNTU kernel: Console: switching to colour frame buffer device 240x67

Is there any way to figure out from the journal output what was the cause of entering Emergency Mode ?

---

### Post by yancek on 2023-07-20
>  Line 243 shows ESP is trying to boot from an UUID that does not exis

The above quote is from the last post by oldfred.  If you look at line 243 in boot repairs output, you will see that UUID (search.fs_uuid 4736ceea35071e15 root)   Line 166 and 167 show the UUIDs for sdb3 and sdb4 respectively and neither is what is shown on line 243 (the grub.cfg entry on the EFI partition)
Beginning at line 316, you see the entries for sdb4 and its fstab file which shows the UUID: d60db62f-b21c-4874-8f6f-16d1a8dbf265 for the / (root filesystem)  which you can see from the blkid output that is the UUID of sdb3, on line 166.  

Also, if you look at the /etc/fstab file for sdb3 and sdb4, you will see that they are identical which is obviously not correct.  I'm not familiar with zfs but it appears it makes some changes to the grub files as they do not appear to have standard entries.

If you haven't resolved this I would suggest again running boot repair with both the original and cloned drives attached and indicate which drive is the cloned and which is the original in your next post.

---

### Post by MAFoElffen on 2023-07-20
boot-repair is not going to fix this. It is not a Grub2 problem.

Do you know how ZFS pool definitions work?

Look at this part of your logs:
```

&#9617;&#9617; A start job for unit systemd-pstore.service has finished successfully.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 552.
Jul 19 10:05:52 ZITO-UBUNTU zpool[1322]: cannot import 'zpool2': invalid vdev configuration
Jul 19 10:05:53 ZITO-UBUNTU zpool[1322]: cannot import 'zpool3': no such pool or dataset
Jul 19 10:05:53 ZITO-UBUNTU zpool[1322]: nvpair_value_nvlist(nvp, &rv) == 0 (0x16 == 0)
Jul 19 10:05:53 ZITO-UBUNTU zpool[1322]: ASSERT at ../../module/nvpair/fnvpair.c:586:fnvpair_value_nvlist()
Jul 19 10:05:53 ZITO-UBUNTU systemd[1]: zfs-import-cache.service: Main process exited, code=killed, status=6/ABRT
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit zfs-import-cache.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'killed' and its exit status is 6.
Jul 19 10:05:53 ZITO-UBUNTU systemd[1]: zfs-import-cache.service: Failed with result 'signal'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit zfs-import-cache.service has entered the 'failed' state with result 'signal'.
Jul 19 10:05:53 ZITO-UBUNTU systemd[1]: Failed to start Import ZFS pools by cache file.
&#9617;&#9617; Subject: A start job for unit zfs-import-cache.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit zfs-import-cache.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 227 and the job result is failed.

```
Zpools are defined with unique disk identifiers to ID the vdevs and to be able to find them.

To fix this, mount the system to /mnt, chroot into it. Export the pools, that will clear the unique disk identifier from the pool def. Import the pool. That will attach the new unique disk identifier of that vdev. Exited the chroot gracefully. Reboot and test.

---

### Post by danik56 on 2023-07-20
ZFs pools zpool2 & zpool3 do not exist any more.  even on the original system they are not present and that does not prevent the OS to boot up.
pool zpool1 is where Ubuntu 22.04 is installed and it is present and was imported and mounted succesfully when booting from the clone drive.

I did further experimenting.

I had an older image of the original system which was taken for Ubuntu 20.04 before the upgrade to 22.04.
I restored this image into the external SSD drive.
Attached this external drive as the ONLY drive to my backup system, and it came up clean with 20.04 and I was able to login.

Next, I performed a Release Upgrade on the drive I just booted from to 22.04.  This finished successfully.
Next, issued REBOOT.

Grub showed 22.04 as default option, and after 2 min I hit the emergency mode prompt again.  
Here are the last few lines from the Journalctl output:

====================================================================
Jul 20 17:38:35 Z2OPEN-B systemd[1]: Finished Raise network interfaces.
&#9617;&#9617; Subject: A start job for unit networking.service has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit networking.service has finished successfully.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 117.
Jul 20 17:38:35 Z2OPEN-B systemd[1]: Finished Load AppArmor profiles managed internally by snapd.
&#9617;&#9617; Subject: A start job for unit snapd.apparmor.service has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit snapd.apparmor.service has finished successfully.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 239.
Jul 20 17:38:39 Z2OPEN-B systemd[1]: Received SIGRTMIN+21 from PID 302 (plymouthd).
Jul 20 17:38:39 Z2OPEN-B systemd[1]: Received SIGRTMIN+21 from PID 302 (plymouthd).
Jul 20 17:38:39 Z2OPEN-B kernel: fbcon: Taking over console
Jul 20 17:38:39 Z2OPEN-B kernel: Console: switching to colour frame buffer device 240x67
====================================================================================

So obviously there is some issue in 22.04 that did not exist in 20.04 before the upgrade.
One other thing I wanted to mention that on this backup system the screen is attached via HDMI.
I know that in 22.04 Wayland replaced XORG as the console interface. Maybe my problem is related to that ?

---

### Post by MAFoElffen on 2023-07-20
What is the /proc/cmdline again? I guess I could recheck the boot-info report where it has that.... At the point it stops... Can you toggle to a vtty via <Cntrl><F4>?

I have an idea... When you import the pools, what it the output of
```

sudo zpool status -v

```

---

### Post by danik56 on 2023-07-20
Thanks for all the advise.  I figured out the cause of this problem.
in /etc/fstab there were 3 automount lines for devices not existing on the backup machine.  so the mount fails for all 3.
In 20.04 it didn't cause a boot issue but on 22.04 it does.
Commented out those 3 auto mounts and backup system is up and runing.
I am surprised the journalctl output didn't clearly say this was the cause for entering emergency mode.

---

### Post by MAFoElffen on 2023-07-20
Very true. It should have thrown a mount error on device not found.

Glad you found the problem. So you can now mark this as "Solved"?

---

### Post by danik56 on 2023-07-21
Done

---

