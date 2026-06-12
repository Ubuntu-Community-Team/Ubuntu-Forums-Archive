---
title: "Failed to connect to lvmetad"
date: 2019-07-29
forum: General Help
---

### Post by umoss on 2019-07-29
My laptop host has Ubuntu installed with hard drive encryption, so I enter the password on every restart.
I also have Virtualbox installed and run several VMs from time to time. Everything worked fine for quite a while.

Then there was an error starting a VM guest yesterday and I decided to rebooted the host to give it a fresh start.

During reboot, I entered the (correct) password and got the following screen message:

  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
  Volume group "ubuntu-vg" not found
  Cannot process volume group ubuntu-vg
No key available with this passphrase.
  WARNING: Failed to cennect to lvmetad. Falling back to device scanning.
  Reading all physical volumes. This may take a while...
  Found volume group "ubuntu-vg" using metadata type lvm2
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
  2 logical volume(s) in volume group "ubuntu-vg" now active
/dev/mapper/ubuntu--vg-root: clean, 246013/15491072 files, 58876300/61932544 blocks
_


This ends the boot process, just the cursor and nothing happens.
Just in case - yes, I entered the password correctly.

I already searched the net for a solution but could not find a good match.
Switched the laptop power off, same result after restart. 
Guess I have to use a recovery console, but do not really know what to do. This is beyond my (poor) linux skills...

So, any advice would be very much appreciated.

---

### Post by TheFu on 2019-07-29
Google found this [https://askubuntu.com/questions/1032885/after-upgrade-17-10-18-04-i-get-failed-to-connect-to-lvmetad](https://askubuntu.com/questions/1032885/after-upgrade-17-10-18-04-i-get-failed-to-connect-to-lvmetad) with links to a bug for 18.04. You didn't provide the release.

Before you get started, while the system is booted, gather some data. You'll need it.
```
sudo lvs
sudo vgs
sudo pvs
lsblk
sudo cryptsetup luksDump /dev/sdaX   # so you have the "name" of the encrypted partition where all the LVs and VGs reside.

```Store that data in files you can access on a tablet or some other computer or just print it out on paper.

I would guess there is some sort of corruption. It could be caused by a software error, a cable or a failing disk.
So, first, I'd check the SMART data for the disk looking for any issues.  Assuming that doesn't look bad, I'd boot from alternate media, install the lvm and cryptsetup tools, "open" the LUKS device manually, have LVM scan and activate any VGs, then manually run fsck against any LVs.

Of course, before starting any of this, I'd 100% know that my backups were working and know how to recover using them.  Some data corruption problems with encryption have only 1 solution - wipe and restore.  You might need to restore from a backup version prior to the corruption problem, so I hope you have a few weeks of daily backups.

If you need some command hints, ask, but you'll have to figure out the options specific to your system. They won't be the same as mine or most other people's.

---

### Post by umoss on 2019-07-31
Thanks TheFu,

 for your detailed advices. Most of them go beyound my ubuntu / linux skills, unfortunately.
Nevertheless, I've found in the meantime the solutioin for my case. I describe it here for others that might experience the same unexpected situation.

I found a related thread here: [https://ubuntuforums.org/showthread.php?t=2396053](https://ubuntuforums.org/showthread.php?t=2396053), linking the issue to kernel version or the deinstallation of nvidia drivers.
Fortunately, another user replied already here: [https://askubuntu.com/questions/969917/failed-to-connect-to-lvmetad-stuck-on-boot/1003374](https://askubuntu.com/questions/969917/failed-to-connect-to-lvmetad-stuck-on-boot/1003374) that none of the advices had helped, but he found out himself that the hard drive had run out of free disk space.

That was also my solution. I deleted some larger files by booting into recovery mode and from then on the lvmetad error was gone and booting worked normally as before.

It was true, I tried to copy a large file the evening before. The process came up with a "not enough disk space" error and I canceled the copying.
I expected somehow that the OS would free the allocated disk space from an unsuccesful file copy, which was not the case and led to the later boot problems.

Anyway, thanks for your support. I'm more than happy to see the laptop running again.

---

