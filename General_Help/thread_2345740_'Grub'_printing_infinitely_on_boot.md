---
title: "'Grub' printing infinitely on boot"
date: 2016-12-07
forum: General Help
---

### Post by sanzybones on 2016-12-07
I was using my laptop normally, 3 hours ago, running Ubuntu.
I clicked to suspend, but it didn't want to suspend no matter what, so I just shut it down with the button.
And now, whenever I start the laptop, it's just a black screen printing 'grub' forever.
By the way, I have Ubuntu installed alongside Windows.
At the moment before suspending, I was accessing some Windows files on Ubuntu. Just viewing, not saving anything.
My guess is that's why it's all messed up, I shut it down forcefully while it had Windows mounted.
Also, when I press F2 to go to the setup window, Boot Option #1 Ubuntu and Boot Option #2 Windows Boot Manager both say "Drive not present"
Did I actually mess up my HDD with this?

---

### Post by oldfred on 2016-12-07
How did you force shutdown. It can corrupt file systems if in the middle of something.
You may need chkdsk on NTFS which can only be run from Windows or Windows repair flash drive.
And you may need fsck from your Ubuntu installer or repair disk.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[URL="http://kember.net/articles/reisub-the-gentle-linux-restart/"]http://kember.net/articles/reisub-the-gentle-linux-restart/

      [/URL]
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 
    [URL="http://kember.net/articles/reisub-the-gentle-linux-restart/"]
[/URL]

---

### Post by sanzybones on 2016-12-07
Thank you for the reply!
I tried what you've said with a Linux flash. I checked my partitions, and Ubuntu was on sda10. I runned the commands on that partitions.
No errors at all showed up. I rebooted, and BIOS still doesn't recognize the hard drive. Could this actually be a hardware problem?

---

### Post by oldfred on 2016-12-07
Lets see if this shows anything:
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

If hard drive is older, you can in Disks utility and icon in upper right corner open Smart Status and see what it says about drive. All I know is good/bad, but it can also run extended tests.

---

### Post by sanzybones on 2016-12-07
Alright, here's the report it generated:
[http://paste2.org/67WJkt4C](http://paste2.org/67WJkt4C)

---

### Post by oldfred on 2016-12-07
You have an UEFI system with Windows & Ubuntu installed in UEFI boot mode.
But you have a grub installed into the MBR for BIOS boot which will never work. Make sure UEFI boot is the default boot mode.

But it also looks like the ESP - efi system partition on sda1 has corruption as files are not shown.

You can use Windows chkdsk or dosfsck from Linux.

       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by sanzybones on 2016-12-08
In my BIOS, UEFI was already the default boot mode.
I tried the dosfsck command. First, I used 'umount' on sda1 but it was already unmounted.
The dosfsck command just gave me "Read 512 bytes at 0:Input/output error"

---

### Post by oldfred on 2016-12-08
If you mount sda1 can you see the /EFI/ubuntu and /EFI/Microsoft folders, perhaps others?

Another fix is to backup all the files & folders in the ESP. Use gparted to delete ESP. Then create new FAT32 partition in same place & size and add boot flag. Then restore backed up files.

You may have to cold (full power down) a couple of times, but UEFI is supposed to find entries in ESP.
GUID of new partition will change so old entries in UEFI will not work. If a drive is disconnected UEFI also loses entries and has to find them.
If UEFI does not find them we can re-add with efibootmgr or reinstall grub using Boot-Manager which would also add new UEFI boot entries.

If you have to create new partition, post this after. You may want to make copy before hand to know all the entries you currently have.
sudo efibootmgr -v

---

