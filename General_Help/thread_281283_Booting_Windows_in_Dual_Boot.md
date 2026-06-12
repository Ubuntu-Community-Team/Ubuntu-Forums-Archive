---
title: "Booting Windows in Dual Boot"
date: 2006-10-20
forum: General Help
---

### Post by AT-AT on 2006-10-20
I've tried using GRUB and LILO but every time I select windows to boot it says "Invalid System disk, replace disk and try again". I'm thinking this may be because Ubuntu decided to name the Windows partition /media/hda1. How do I rename it and what do I rename it to?

---

### Post by catlett on 2006-10-20
Do you have a floppy in the flopy drive or a cd in the cd drive? That is usually the error when the computer boots to a floppy or cd drive and the disk isn't bootable. 
The windows partition isn't renamed. That is just how ubuntu identifies it. It is still your C drive in windows. To further explain, linux uses one tree where windows uses multiple trees. Linux starts the tree at root and everything is mounted underneath. Windows uses C (usually) as the main tree but will make others for cd drives or other partitions (i.e. D,E and so on).
 The hard drive in linux is labeled hd for an abbreviation of [COLOR="Red"]h[/COLOR]ard [COLOR="Red"]d[/COLOR]rive. The first Hard drive is labeled with an a ( [COLOR="Red"]h[/COLOR]ard [COLOR="Red"]d[/COLOR]rive [COLOR="Red"]a[/COLOR]...hda) and the first partition is labeled 1. So your first partition of your first hard drive is hda1. It is a [COLOR="Red"]dev[/COLOR]ice so it is prefaced with dev for a label of  /dev/hda1
Since everything is under root, things need a place to be mounted. Being that a hard drive is a form of media, ubuntu mounts a partition from a hard drive in media. So your windows partition is mounted in the media directory as a folder bearing it's name hda1. Thus to ubuntu your windows partition is /dev/hda1 and it is mounted at /media/hda1 but none of this is affecting anything on your windows partition. This is solely an internal labeling of the drive in linux. Your windows partition in windows will still be C.
The error is consistent with leaving a floppy in the drive that isn't bootable. Check your drives for a floppy or cd and remove them before booting. Hopefully it is as simple as that.

---

### Post by AT-AT on 2006-10-20
Its not that simple. I have LILO in the MBR (GRUB wouldnt install for some arcane reason), and have nothing in optical or floppy drives. I call up the screen to choose Windows and it says "Invalid system disk...". I found something called a Super GRUB Disk (a CD iso for grub bootable disk) and it said the same thing as LILO.
 
If push comes to shove, I want to reformat my drive and reinstall both OSs, however I dont know how to that (since I only have 1 HDD, and not 2).

---

### Post by catlett on 2006-10-20
You can use gparted live to reformat your drive.[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It is a live cd. You download the iso and burn it to a cd. Then boot to the cd. Then you can delete all your partitions. Then you can make a new partition. Gparted can only make a fat32 partition but windows installer can format it to ntfs during the install.
Install windows first. Give it the whole drive. It will make one ntfs or you can choose to keep it fat32 if you want linux to be able to write to it after both OSs are installed.
After windows is installed, boot to the Ubuntu installation cd. It has an option to shrink the existing windows partition and install ubuntu on that space. Ubuntu can install on 3gb but 10gb would keep plenty of free room. Obviously if you have a large drive, you can make it larger. This how to shows the part about shrinking the windows partition.[http://www.psychocats.net/ubuntu/installinPost](http://www.psychocats.net/ubuntu/installinPost) if you have any questions post.

---

### Post by ReaderRat on 2006-10-20
Just be sure and install Windoze first, and the installer will set up a dual-boot.

Also:  [**Dual-Booting (One HDD)**](http://users.bigpond.net.au/hermanzone/)

---

### Post by AT-AT on 2006-10-20
I guess I should note that the computer Im talking about is rather old; 1999-ish with Win 98, though it did receive a 120 GB HD upgrade.

---

### Post by AT-AT on 2006-10-21
I've pretty much been able to wipe my HDD and reinstall Win98. However my restoration CD didnt restore the MBR. Will using a bootable floppy made from WinXP be able to restore the MBR, and if so, how? If not, what do I need to do? Thanks.

---

### Post by catlett on 2006-10-21
There is a command for restoring the mbr in windows. I know it is on the XP installation disk as part of the 'recovery console'. Anyways the command is ```
fixmbr
```There is also a ```
fixboot
``` command. Try those from the floppy to see if it will work for your 98 edition and I'll search for a rescue disk you can download and try.

WAIT A MINUTE, I JUST FOUND SOMETHING.

Boot to a dos floppy and issue this command at the "A" prompt (i.e. A:\> )
Then enter this command
```
FDISK.EXE  /MBR
```

P.S. I got the last command from this
> The simplest way to repair or re-create MBR is to run Microsoft's standard utility called FDISK with a parameter /MBR, like

	A:\> FDISK.EXE  /MBR

FDISK is a standard utility included in MS-DOS, Windows 95, 98, ME.
Found here [http://www.ntfs.com/mbr-damaged.htm](http://www.ntfs.com/mbr-damaged.htm) Just in case you want to look into it some more.

---

### Post by AT-AT on 2006-10-21
Hmmm, did the FDISK.EXE /MBR, and lilo was erased (yay!), but now its telling me that the HDD is not a bootable disk. No clue where to go from here.

---

### Post by catlett on 2006-10-21
> **AT-AT said:**
> Hmmm, did the FDISK.EXE /MBR, and lilo was erased (yay!), but now its telling me that the HDD is not a bootable disk. No clue where to go from here.
Since you have just re-installed and you do not have any data on the drive, I would re-install windows again. When I am in a situation like this, I re-install. There isn't any data to worry about and you can spend more than the hour it takes to re-install looking for answers that do not work.
I would assume that since the mbr is back to a windows format, the install will be bootable after re-install. 
There may be a simple solution but I do not know it. Unless someone with more windows experience offers advice, I would re-install.

---

### Post by AT-AT on 2006-10-21
Okay then, that sounds like a good idea. Thanks.

---

### Post by gn2 on 2006-10-21
> **AT-AT said:**
> Okay then, that sounds like a good idea. Thanks.

If you've still got W98se, I would recommend looking for a cheap copy of W2000Professional on eBay.

Easily Microsoft's best effort to date.

---

