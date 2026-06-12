---
title: "Grub Error/ Partition Woes"
date: 2006-11-05
forum: General Help
---

### Post by redbluemangle on 2006-11-05
Ok so heres the deal, 

I have 2 HDD's I had one for WinXP and one for Ubuntu. Ubuntu was only using a tiny fraction of the disc so(using the live CD) I ran Gpart and resized the ext3 partition and made a fat32 one in the newly freed space. I got some errors about the disc being busy and the operations were bungled.

It seems I have erased my main linux partition.

The problem is, even though I have WinXP on a seperate disc, GRUB is now messed up and when I boot I get "Error 15" grub and no boot loader is loaded.

](*,) Am I screwed?

---

### Post by Kateikyoushi on 2006-11-05
This will fix your MBR so you can boot XP.

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

---

### Post by bulldog on 2006-11-05
You can't resize mounted disks in the first place,if you did nothing will happened I suppose.
You have to do so from a live cd or a Gparted cd and boot one of them.

15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

This error looks not to bad to me.

I think you have to look if everything is allright with your menu.lst.

---

### Post by redbluemangle on 2006-11-05
"This will fix your MBR so you can boot XP.

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer"

I apreciate this greatly however, by restoring as you have stated will it be my XP installation, as I left it? 

Also, how would I go about making a partition that is readable from both windows and Ubuntu?

---

### Post by Kateikyoushi on 2006-11-05
That restores your MBR so it boots windows automatically. I thought your linux partition is broken so you want to use at least one OS.
You could use the livecd (which you probaly used to install ubuntu) to create and resize partitions, run gparted from the disc.
Instead of using a separate partition to move data from windows to ubuntu you could use the ext driver to read and write your linux partition from windows. [LINK]("http://www.fs-driver.org/")

Post us your /boot/grub/menu.lst file and your partition information so we can edit your grub.

```
sudo fdisk -l
```

---

### Post by redbluemangle on 2006-11-05
Ok I can now boot up my XP so thats good :D

I was running Gpart from the live CD yet I still managed to ruin my Ubuntu install. The main partition went from 4.5Gb to 450Mb.

What I did is got Partition Logic, a standalone partitioner and deleted all the linux partitions and I have made a Fat32 partition and left adequate space for installing Ubuntu.

---

### Post by Kateikyoushi on 2006-11-05
Weird because it shouldn't let you to make the partition smaller than the disc space used by the data on that partition.

---

### Post by redbluemangle on 2006-11-05
hmmm well I've reinstalled Ubuntu but as a nix-noob I have no idea how to access my fat32 partition. Its located at /dev/hdd3. I should have read access to fat32 shoudlnt I? I noticed when I was manually editing the partition table, I could assign mount points for any partitions, should I have given it a mount point?

---

