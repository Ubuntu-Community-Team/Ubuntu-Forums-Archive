---
title: "Flashing cursor instead of boot following power cut."
date: 2013-10-29
forum: General Help
---

### Post by Windoze Refugee on 2013-10-29
After the storm yesterday we had a couple of power outages, and following one of these I've ended up again with this issue where I cant boot into Ubuntu and instead it halts at the flashing cursor.
 I've tried running in recovery mode, but it hangs at :
0.009704 ACPI : Core revision 20110623

I've tried running Testdisk from within Ubuntu live from the CD and got to see the drives all intact. I can also access all the data so that at least seems safe (phew). But in all honesty I've had trouble deciphering the instructions in Testdisk so not sure I've managed to do the right thing there.

The results of the test are here [http://paste.ubuntu.com/6320431/](http://paste.ubuntu.com/6320431/)

I also ran Boot repair disk and re-installed the grub, and that at least seems normal. 

Also, for a while its been posting the following at first start up,
"Reboot and select proper Boot device or insert Boot Media in selected Boot device and press a key". 
This is usually resolved by just pressing the reset switch on the tower.

Does anyone have any ideas?
Very grateful for any help or suggestions.
Cheers
WR

---

### Post by Windoze Refugee on 2013-10-29
In case it's of any use to some kind soul who'll help me fix this damn thing (please dear god) I've also run this, as per another victim's thread:

ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 189.9G  0 disk
&#9492;&#9472;sda1   8:1    0 189.9G  0 part
sdb      8:16   0 465.8G  0 disk
&#9500;&#9472;sdb1   8:17   0   128G  0 part
&#9500;&#9472;sdb2   8:18   0 138.6G  0 part
&#9500;&#9472;sdb3   8:19   0     1K  0 part
&#9500;&#9472;sdb5   8:21   0 127.4G  0 part
&#9500;&#9472;sdb6   8:22   0   5.4G  0 part [SWAP]
&#9500;&#9472;sdb7   8:23   0  63.7G  0 part
&#9492;&#9472;sdb8   8:24   0   2.8G  0 part [SWAP]
sr0     11:0    1   707M  0 rom  /cdrom
loop0    7:0    0 675.2M  1 loop /rofs

ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.7G  301M  1.4G  19% /
udev            1.7G  4.0K  1.7G   1% /dev
tmpfs           667M  824K  667M   1% /run
/dev/sr0        707M  707M     0 100% /cdrom
/dev/loop0      676M  676M     0 100% /rofs
tmpfs           1.7G   16K  1.7G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            1.7G   88K  1.7G   1% /run/shm

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Maxtor 6Y200M0 (scsi)
Disk /dev/sda: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  204GB  204GB  primary  ntfs         boot


Model: ATA ST3500630AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  137GB  137GB   primary   ntfs            boot
 2      137GB   286GB  149GB   primary   ntfs
 3      286GB   500GB  214GB   extended
 7      286GB   355GB  68.4GB  logical   ext4
 8      355GB   357GB  2953MB  logical   linux-swap(v1)
 5      357GB   494GB  137GB   logical   ext4
 6      494GB   500GB  5832MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system). 
/dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by Windoze Refugee on 2013-10-29
I've also run the diagnostic from within Ubuntu Live (ie from the disk) and it came up with a complete fail on the video card! Is it possible that all this is a result of the GPU failing from a power surge? Ie Would a video card fail prevent the boot?

---

### Post by whitesmith on 2013-10-29
This is easy to say after the cows have left the corral, but never have a computer of any value connected directly to the mains. Always use a UPS. I'm not sure that a dead video card would prevent booting, but stuff might be on the screen and rendered invisible by a zombie card. I'd try swapping out a known good card just to be sure.

---

### Post by Impavidus on 2013-10-29
I know that storm, quite a few households in the UK and France lost electric power. (Here, having a buried mid-voltage network paid off. No outages for years.)

A power surge could cause damaged hardware, but as you can still boot the live disk (or a boot-repair disk) I doubt it's that. It could be a corrupted file vital to your system, especially if you were running an update when the power failed. I see you have quite some old kernels, an old Ubuntu 9.10 and Win XP on that machine. Can you boot any of those? If you can boot your 12.04 using an old kernel, do that, else you need to boot your old 9.10 or a live disk and try to fix your system using a chroot: [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels) (you need to adapt it to your situation, but it tells how to chroot). I never really tried that myself, so I don't know the details.

Once you have booted your 12.04 or have chrooted into it, check the package management system. It may need repair.

---

### Post by Windoze Refugee on 2013-10-29
HI Guys and thanks for your input. Without wishing to sound like a total dunce, what's chroot? 
And do you think it will fix the problem?
Cheers
WR

---

### Post by kdomrose2 on 2013-10-29
I had a similar issue. I was able to fix it by booting to a terminal only. No GUI.
Then I used either startx command or xinit. I can't recall which one right now. Basically you have hosed files for X  right now.

---

### Post by Impavidus on 2013-10-29
I never really used it either, so I don't know exactly, but you can use it to make command execute in a directory tree different from the running system. This allows you to use tools like apt-get and the like to fix your system whilst running a different system. The link I posted gives an example on how to use it, and better than I could tell you. It may solve your problem.

---

### Post by Windoze Refugee on 2013-10-30
Thanks for that. I'll look into chroot. 
Meantime, I remember that I had also just done a software update.
Given that I can only run CD live version of Ubuntu if I uncheck the ACPI option (F6 during boot sequence) and that the ordinary recovery boot hangs at the same ACPI, does anyone think it may be to do with this video (?) update, and ifso, how I might go about undoing the damage?
Cheers 
WR

---

### Post by steeldriver on 2013-10-30
What **version** of ubuntu and **what video card** do you have

A recent update on my 12.04 laptop with nvidia graphics updated to an unusable driver version, with exactly the 'flashing cursor' symptoms you are describing - solution was to boot into recovery mode and downgrade the driver. But we need more information to diagnose.

---

### Post by Windoze Refugee on 2013-10-30
Im using 12.04 and my card is an nvidia : VESA: nv44 Board - p382h1.
But I'm unable to boot into recovery as it hangs at the ACPI line :(
Cheers for your input 
WR

---

### Post by Windoze Refugee on 2013-10-31
Can anyone advise how to boot into recovery mode when it always hangs before completing?
Cheers
WR

---

### Post by steeldriver on 2013-10-31
If you absolutely can't boot even into recovery mode, then you may need to chroot from the live CD

I took a look at your boot info pastebin and tbh it's beyond my paygrade (seems to be a lot of complicated RAID stuff?) - sorry

---

### Post by Windoze Refugee on 2013-10-31
It seems like the problem is with the nvidia video driver that got updated, but its hanging the boot whether in the usual 12.04 kernel or the recovery mode :( . 
Im looking into chroot at the moment, but I'm finding it a bit overwheleming :( . 
I think I went in too hurriedly trying to fix it before and may have moved the boot in to the wrong partition too :( 
I rebult the grub using the boot recovery tool but I'm not sure its ended up in the right place, and either way Im not sure how to get to the place I need to downgrade the graphics driver, or in fact what to do if/when I get there :( :(

---

### Post by steeldriver on 2013-10-31
Can you at least get to the grub menu? if so you should be able to edit the boot command (press 'e') to add 'nomodeset' which will hopefully force a fallback to an open source radeon or plain VESA driver - that will be easier than chrooting, if it works

---

### Post by Windoze Refugee on 2013-10-31
OK. Ive tried that but with no success :( It returns an error : "unknown command nomodeset" 
Does it need to go in a particular line or is there some parameter I need to include as well?
Cheers
WR

---

### Post by Impavidus on 2013-10-31
You could try the nomodeset, although that option is also used automatically in recovery mode, which doesn't work.

You tried the regular 12.04 and the recovery mode. Did you also try old kernels, maybe in recovery mode too (in the grub menu, select "Previous Linux versions" and then select one of the old kernels)? You could also try booting "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb7)" (one of the last entries in your grub menu). If it works, it will give you an old Ubuntu, which, although not very secure anymore, may be more responsive than a live disk and should also allow you to chroot into your 12.04 system.

---

### Post by Windoze Refugee on 2013-10-31
Nope. No matter which version I try it hangs every time at the same point: "[0.009770] ACPI: Core revision 20110112
ArggggggggggggggggHHH!!!

I was following the instructions here [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels) and managed to get into the Chroot, did the update and installed a 'fresh' version of 12.04 (at least I think idid) but if the embeddded video drivers for that update are whats causing the problem, Im not sure what else I can try :(

---

### Post by steeldriver on 2013-10-31
maybe before exiting the chroot, use jockey-text to disable the offending driver?

```

# jockey-text --list

# jockey-text --disable xorg:nvidia_319

```

(assuming that's the troublesome one) - it should fall back to the previous version, but run --list again to check

---

### Post by Windoze Refugee on 2013-10-31
I've managed to get it to boot woo hoo:)
I used boot repair disk advance options to modify the grub and disable the ACPI load.
It doesnt seem to have impeded performance at all, but this feels like a bit of a heath-robinson fix. Any idea about how to roll back the driver to an earlier version, or will not having ACPI not cause any real probs?
Cheers
WR

---

### Post by steeldriver on 2013-10-31
Well if you can boot into the Ubuntu desktop, you can use System Settings --> Additional Drivers to roll back. Otherwise see the jockey-text instructions in my previous post.

---

### Post by Windoze Refugee on 2013-11-03
Many thanks for your input steeldriver

---

