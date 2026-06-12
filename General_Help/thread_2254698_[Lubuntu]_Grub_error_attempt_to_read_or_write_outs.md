---
title: "[Lubuntu] Grub error: attempt to read or write outside disk 'hd0' after upgrade"
date: 2014-11-29
forum: General Help
---

### Post by jim1944 on 2014-11-29
The problem referred to in the title has magically gone away but I'd like to understand what happened.

Because of the problems discussed in [http://ubuntuforums.org/showthread.php?t=2253931](http://ubuntuforums.org/showthread.php?t=2253931) I decided to upgrade from Lubuntu 14.04 to Lubuntu 14.10. I went through that process but at the reboot I got this error:
```
Error: attempt to read or write outside disk 'hd0'
Entering rescue mode...
grub rescue>
```

Having no idea what to do in rescue mode, I poked around on the internet and found Boot Repair and tried its recommended fix. Upon reboot I got the same error message but instead of going into rescue mode it said, "Press any key to continue..." Couldn't find the 'any' key :-), so I pressed enter. Nothing happened so I pressed the space bar. Again nothing happened. In retrospect, I may not have waited long enough.

Note: as a result of the Boot Repair, I started to get a boot menu that included ubuntu and a couple of memory check options. Had never seen that before. Always had just booted directly to Lubuntu which was the only OS on the machine. The error occurs upon pressing enter at the boot menu with ubuntu selected. It appears to me that the recommended fix that Boot Repair performs seems to be a reinstall of grub, a grub update and some grub configuration.

Anyway, I shut down the computer, booted into an Lubuntu 14.10 live CD, reinstalled and updated grub, and rebooted. I got the same thing as I had after doing Boot Repair but this time I got a little side tracked after pressing enter at the "Press any key to continue..." prompt and , lo and behold, after a while it booted up successfully. (As I sad previously, maybe I didn't wait long enough when I booted after to doing Boot Repair.)

So I rebooted. This time I got no error message but during the boot up I got an orange screen with horizontal streaks before the login screen came up. I logged in and rebooted and got neither an error message nor the orange screen - a completely normal boot up (still with the boot menu that I got after doing Boot Repair). I have done several reboots since then without incident.

So everything seems to be working now but what happened?

Thanks
Jim

---

### Post by oldfred on 2014-11-29
How old is hardware?
And can you set BIOS to use AHCI for hard drive, not IDE nor RAID?

If in IDE mode or very old BIOS you may not be able to have any boot files beyond 137GB on drive. If newer larger drive in old system, and you have just / (root) and swap you may at random have boot files anywhere on drive. 

If that is the case, better to have smaller / of 20 or 25GB and use rest of drive as /home or just as data. Many older instructions suggest separate /boot but if all of / is inside the first 137GB then separate /boot not required.

Also sometimes partition tables get written where extended partition is beyond the end of the drive. Testdisk has been known to do that as it converts from CHS cylinders, heads, sectors to LBA sectors and rounds incorrectly.

---

### Post by jim1944 on 2014-11-29
I like the 137 GB limit theory. It would explain why I've had a couple of booting issues after software updates.

The hard drive is a 160GB IDE which was empty when I installed Lubuntu 14.04, letting the installer partition the drive as it pleased. It created two partitions, /dev/sda1, the root partition of 148.30 GB, and /dev/sda5 inside the extended partition /dev/sda2, a 766.00 MB swap partition. So /boot files could be placed beyond the 137 GB limit assuming that files are not added to a drive from, physically, beginning to end (there's only a bit less than 7 GB of used space on the sda1 partition). 

Can I use gparted to shrink sda1 in place to less than 137 GB and avoid this problem?

Is there a way to confirm that the BIOS has this 137 GB limitation? The machine was built by my son and I around 2001.

Finally, is the limit 137X1024^3 or 137,000,000,000?

Thanks
Jim

---

### Post by oldfred on 2014-11-29
History of BIOS and IDE limits
[http://tldp.org/HOWTO/Large-Disk-HOWTO-4.html](http://tldp.org/HOWTO/Large-Disk-HOWTO-4.html)
Out of disk error add to grub install disk-module=ata or use Boot-Repair ATA Disk support
HOWTO: dualboot on big disk (BIOS limitations)
[https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)
[http://ubuntuforums.org/showthread.php?t=1998257](http://ubuntuforums.org/showthread.php?t=1998257)
Large external drive still needed /boot at beginning:
[http://ubuntuforums.org/showthread.php?t=1888497](http://ubuntuforums.org/showthread.php?t=1888497)

My normal suggestion is to use 25GB for / (root) and the rest as /home or just as data partition(s).
You should be able to use gparted to shrink sda1, I have suggested that many times, but only in about half of those has that worked.

Linux ext4 partitions have data randomly(?) written to drive. Where Windows tends to write everything at beginning of drive, but then drive becomes very fragmented over time. Linux writes entire file if new write is larger and in another location.

Often the summary report from Boot-Repair shows the locations on the hard drive of grub & kernels. And those can be anywhere. Now with multiple TB sized drives just having one very large / does not make sense. Drive has to jump all over for just the boot files. So a smaller root also makes sense for new larger drives. Reading data that can be anywhere on drive is ok.

---

### Post by jim1944 on 2014-11-30
I resized /dev/sda1 to about 120GB to prevent any boot files being written above the 137GB line and rebooted. The reboot was successful but during the boot up it presented a purplish screen with horizontal streaks before the login screen came up. This was similar to the orange screen I had seen previously and since that did not repeat I tried another reboot. But it did repeat. So I reinstalled and updated grub and rebooted and this time I got no funny colored screen during boot up.

Since the machine was built around 2001 which would be about the right time frame for a 137GB BIOS limitation, I am going to assume that my boot problems have been related to that and are now solved. So I'm marking the thread solved.

Thanks oldfred.

Jim

---

