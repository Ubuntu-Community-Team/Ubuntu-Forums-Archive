---
title: "windows update trashes wubi: how to recover"
date: 2012-10-26
forum: General Help
---

### Post by john_3000 on 2012-10-26
This is a solved problem I want to share, showing everything in one place.

After successfully booting my Samsung netbook NC10 into wubi-installed Ubuntu 12.10 Linux many times, one day it started failing and dumping me into Busybox with an (initramfs) prompt. After 2 days of Googling and trial and error, the following steps are what it took to repair my broken system.

0  I think maybe the problem was caused when I updated Windows XP. The updates called for a reboot of Windows.  But instead of immediately rebooting into XP I absently booted into wubi Ubuntu. Thereafter Ubuntu was trashed. XP remained OK and finished the upgrade normally when I returned.

1  The answers that worked are here:
      [http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

2  If you don't already have one, make a live Linux USB stick. Staying with Ubuntu,

2a  Download the appropriate .iso file from ubuntu.com

2b  Check the md5 sum against the one here:
      [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
I did this in Windows using md5sum.exe from etree.org (it's free). I had to download the .iso file a second time to get the right hash.
      
2c  Download a live stick burner that works in Windows. Ubuntu recommends the one at pendrivelinux.com

2d  Burn the stick.  NOTE: I had to check the "format" box. Step 3 would not work without formating the stick.  If necessary adjust your bios to allow booting from USB. 

3  Boot into the stick. Select "try", not "install"  If it's Ubuntu, enter "terminal" in the ridiculous Unity search field to get a command line.

4  Then in order, (from the neosmart.net thread)

4a Find which drive/partition has the wubi files:
	sudo fdisk -l

4b Make a mount point for it:
	sudo mkdir /win

4c Mount it.  In my case it was sda3 so
	sudo mount /dev/sda3 /win

4d Make another mount point:
	sudo mkdir /vdisk

4e Mount the wubi file:
	sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

4f In my case command 4e failed so run fsck:
	sudo fsck /win/ubuntu/disks/root.disk

5  fsck worked and worked and worked some more but eventually got things squared away.  Ignoring step 4e, I rebooted without the stick and all was well again.

---

