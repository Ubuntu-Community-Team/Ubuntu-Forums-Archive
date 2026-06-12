---
title: "Please help - System won't boot"
date: 2013-06-21
forum: General Help
---

### Post by KieranFitzgerald on 2013-06-21
Ubuntu 12.10 64 bit.
I have increased my boot sector using Gparted which appeared to work correctly.
System now starts to GNU GRUB version 2.00 version 2.00-7ubuntu11

GRUB> prompt

I assumed I would have to do a boot repair but having downloaded and created a boot repair stick I can not get it to work.

The recommended repair asks me to purge GRUB2 and to type or cut and paste some commands into a terminal.

The first of these commands fails as it can not find the specified directory.

Create a bootinfo summary produces this link

[http://paste.ubuntu.com/5786419/](http://paste.ubuntu.com/5786419/)

Can I fix this system?

Thanks Kieran

---

### Post by KieranFitzgerald on 2013-06-24
More info in the hope that I can revive this system.

Boot sector is /dev/sda1/ ext2

ubuntu on extended sda2  as sda5 lvm2 pv 
I moved this "up" the disk to increase the boot sector because I had problems with upgrades reporting lack of disk space.

Gparted has always worked well for me and I expected to have to repair the boot mechanism.

Please, some guidance.

Thanks Kieran

---

### Post by The Cog on 2013-06-24
If you are able to download and burn a copy of SystemRescueCd [http://www.sysresccd.org/&#8206;](http://www.sysresccd.org/&#8206;) this has an option to boot the first Linux it can find on the hard disk. You can then run the commands:
```

sudo update-grub
sudo grub-install /dev/sda

```
which should do the trick. I have used this in the past after restoring a Linux partition image to a new disk that doesn't have a bootloader at all.

---

### Post by KieranFitzgerald on 2013-06-24
Thanks for the suggestion.
It can't find Linux, perhaps the lvm2 format for the partition is a problem.
Show all partitions does not report /dev/sda5 which exists.

---

### Post by The Cog on 2013-06-25
Ooh. That's nasty. SystemRescueCD also has gparted - does that show the existence of sda5? 

If not then maybe the previous use of gparted went horribly wrong somehow, and you lost the partition entry. testdisk is also on the system rescue cd, and claims to be able to find and recover partitons that have been removed from the partition table.

---

### Post by KieranFitzgerald on 2013-06-25
Gparted shows both the boot (SDA1) and main partition (SDA5)

If I had known lvm2 was such a major hurdle I would have much more careful during the initial installation.  LVM2 is the default!.

There must be someone who can help with this.  My knowledge of the inner workings of linux and its boot mechanism is very limited.

Sorry to gripe but I'm desperate, Please help.

---

### Post by steeldriver on 2013-06-25
> **KieranFitzgerald said:**
> 
The recommended repair asks me to purge GRUB2 and to [B]type or cut and paste some commands into a terminal.

The first of these commands fails as it can not find the specified directory.[/B]

Do you remember what commands? what directory? that may give us some clues (I don't see that information in your pastebin - just that it will "reinstall the grub2 of mapper/ubuntu-root into the MBR of sda")

---

### Post by KieranFitzgerald on 2013-06-25
Sorry I can't remember the commands but it appears that these repair/recovery utilities don't support lvm2.  Probably boot or root on the lvm2 sector are not visible.  If you feel exact details would help i'll set up the boot repair stick and try again.
Other threads suggest that the process of reinstalling grub2 must be done manually but I can't find a definitive set of instructions.

---

### Post by fantab on 2013-06-25
Post the output of the 'BootInfo Summary' which 'Boot-Repair' generates. You can boot Ubuntu live DVD/USB, right?

---

### Post by KieranFitzgerald on 2013-06-25
Done,  see original post.

---

### Post by oldfred on 2013-06-25
I do not know RAID nor LVM. Did you encrypt system as I think that is the only time it uses LVM as default.

Boot-Repair has trouble telling RAID from LVM as both use /mapper. Not sure it it has a setting you manually have to make so it knows it is not RAID?

If Boot-Repair does not work.
       chroot & reinstall grub encrypted LVM
[http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/](http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/)


 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

---

### Post by KieranFitzgerald on 2013-06-25
My version of rescuecd (3.7.0) only has "default" and "boot an existing linux system installed on the disk"

Report Could not find kernel image initrd=/ubninit

---

### Post by oldfred on 2013-06-25
Do not know about the RescueCD. It may not be mounting the LVM and that is why it cannot then find the kernel.

Try Boot-Repair again? 

Or run the manual commands from a Ubuntu liveCD. But you will probably have to manually add the lvm2 driver as the live installer may not have it.
       sudo apt-get install lvm2

---

### Post by YannBuntu on 2013-06-25
hi Kieran

> **KieranFitzgerald said:**
> The first of these commands fails as it can not find the specified directory.

please redo the Recommended Repair, follow instructions, then take 2 screenshots :
1) one screenshot of the Boot-Repair window showing the 3 commands
2) one screenshot of the terminal output showing when the command fails

then please show us the 2 screenshots. (you can upload them on [http://imageshack.us](http://imageshack.us) for example).

---

### Post by KieranFitzgerald on 2013-06-25
Booted from live cd
The lvm2 sector appears to be intact (phew!).

Using showthread.php?t=1984459 

Did the following (sudo with all)
apt-get install lvm2
vgchange -a y
     2 logical volumes(s) in volume group "ubuntu" now active

lvscan
 ACTIVE '/dev/ubuntu/root' 
 ACTIVE '/dev/ubuntu/swap-1'

mount /dev/mapper/cds-root /mnt   edit is there a space before /mnt
 /dev/mapper/cds-root  does not exist

So can't proceed to grub reinstall

---

### Post by steeldriver on 2013-06-25
Based on the boot-repair output, your LV is not called cds-root, it's called ubuntu-root - so the command probably needs to be

```
mount /dev/mapper/**ubuntu-root** /mnt
```

---

### Post by KieranFitzgerald on 2013-06-26
[COLOR=#000000]YannBuntu
I am trying the manual route at present using live usb without boot-repair.
The cut and paste messages were presented just after pressing recommended repair and related to grub removal.
There was a picture of a screen about confirming grub removal below it.
Hope this helps
Nearly a week at this, I am heading towards re-installation of Ubuntu sorry about the sceen shots!
Kieran[/COLOR]

---

### Post by KieranFitzgerald on 2013-06-26
Thanks steeldriver
One step further on
next sudo mount /dev/sda5 /mnt/boot
    unknown file system type 'LVM2_member'


aaarg - this is so frustrating!  I'm no expert with this system related stuff.

re-installation looms.

---

### Post by steeldriver on 2013-06-26
What instructions are you following exactly? afaik your boot partition is sda1 - from your boot-repair pastebin

```

Model: ATA WDC WD10EZRX-00A (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
[COLOR=#0000ff]1      1049kB  302MB   301MB   primary   ext2         boot
[/COLOR]2      302MB   1000GB  1000GB  extended
5      303MB   1000GB  1000GB  logical                lvm

```

I agree with the earlier poster - re-running the recommended boot-repair and posting back with any errors / messages is how I'd proceed at this point - I'm not familiar enough with boot-repair to understand everything it reports, but it seems to be correctly detecting (and even mounting) your LVM volumes so it appears to be 'LVM2 aware', I'm not sure you'll gain anything by doing it manually (unless it fails). I have a 12.04 server box with an LVM root setup and my boot-repair report looks very similar.

---

### Post by KieranFitzgerald on 2013-06-26
Ok
Installed boot-repair on live session.

Running it, getting further

Get as far as 
configuring grub-pc  see shot 2   attached
Whatever the position of the red box pressing enter gives an new screen saying
Continue without installing GUB see shot 3 attached

What should I do here?
Kieran

---

### Post by oldfred on 2013-06-26
I think Yann has you chrooted and running the dpkg. I post this when just running it from inside an working install to update grub. You need arrow keys & spacebar. Do not choose partitions and never ever choose a NTFS partition. In fact we have filed bug reports for years to get them to stop installing the PBR - partition boot sector of NTFS partitions as that damages Windows.

 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by KieranFitzgerald on 2013-06-26
That did it now up and running.  Much easier to do from the live session.
I got confused between the application and the terminal based stuff and missed the section regarding the grub install location.
Thanks very much for your combined help.
Kieran

---

### Post by oldfred on 2013-06-26
Glad you got it working. :)

---

