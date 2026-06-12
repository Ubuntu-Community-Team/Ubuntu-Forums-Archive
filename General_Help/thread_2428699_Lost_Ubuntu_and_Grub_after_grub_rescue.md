---
title: "Lost Ubuntu and Grub after grub rescue"
date: 2019-10-07
forum: General Help
---

### Post by azah197 on 2019-10-07
Hi guys,

I have a dual boot with Ubuntu 18.04 and Windows 10. I had to update my Windows for security reasons. After the update I got the problem Grub rescue. I was able to solve the problem with some YouTube videos. After the restart windows started directly. The Grub menu did not appear. I have learned that my PC does not run on UEFI (in BIOS is Legacy + UEFI) BIOS doesn't show me Windows or Ubuntu. So I can't get into Ubuntu at all. Has my Ubuntu been deleted or am I just too stupid to solve it?
Thanks in advance!

---

### Post by Impavidus on 2019-10-07
Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) from your Ubuntu live disk and create a boot info summary. Show us the link. That should give us good diagnostics.

It's not inconceivable that Windows deleted the Ubuntu partition. It's a known bug in Windows. It's very well possible all data is still on your disk and the partition can be restored (that is, assuming it's a spinning hard disk).

---

### Post by azah197 on 2019-10-07
[http://paste.ubuntu.com/p/mFqXpSmwWG/](http://paste.ubuntu.com/p/mFqXpSmwWG/)

thanks for the help

---

### Post by oldfred on 2019-10-08
This has several issues:

```
/dev/sda4         340,643,838   499,193,855   158,550,018   5 Extended
/dev/sda5     ? 3,329,346,150 4,158,730,476   829,384,327  57 DrivePro

```
  from line 83 in report
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda4

Your sda5 starts & ends beyond drive & is larger than extended partition.
And you have no Linux partition inside the extended partition.
I think you have to fix sda5 first, but am a bit concerned if that may corrupt Linux partition(s).

If your Linux partition is just the size of the extended partition you can do this:

backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print

It seems all BIOS/MBR versions of Windows since Windows 7 on major updates rewrite partition table & "forget" to write Linux logical partitions back into partition table.
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988) &
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition)

You also show Windows 10 is hibernated or fast start up is on. That must be off:
Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by Impavidus on 2019-10-08
It looks like Windows deleted the Ubuntu partition. You got a new partition, sda5, which is supposed to be in the extended partition, but is actually well past the end of the drive.

I've never done this myself, but it may be possible to recover your Ubuntu partition: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Your lost partition starts shortly after sector 340643838 and ends shortly before or at sector 499193855.

---

### Post by azah197 on 2019-10-08
How can I do this step when i cant boot in my Linux?

"[COLOR=#000000]backup partition table before any changes, so you can get back to current if changes not correct[/COLOR]
[COLOR=#000000]sudo sfdisk -d /dev/sda > PT_sda.txt[/COLOR]
[COLOR=#000000]So you know sectors:[/COLOR]
[COLOR=#000000]sudo parted /dev/sda unit s print"


[/COLOR]

---

### Post by oldfred on 2019-10-08
You do it from the live installer. 

You always need a live installer for Ubuntu and if Windows a Windows repair flash drive, so you can repair system.

BIOS versions of Windows 10 are not particularly dual boot friendly. Both the erase partition table on major updates and turning on fast start up with update. 
If fast start up on, then grub will not boot Windows as hibernation flag is set. With BIOS then you have to temporarily restore a Windows boot loader to be able to turn off fast start up or make other repairs, so grub can boot Windows. Then restore grub to MBR to boot. With BIOS better to have two drives, so you have two MBR and can have different boot loaders in each. Or use UEFI if system is newer as you can always boot Windows from UEFI boot menu.

---

