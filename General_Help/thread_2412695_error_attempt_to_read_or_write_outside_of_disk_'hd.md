---
title: "error: attempt to read or write outside of disk 'hd0'"
date: 2019-02-16
forum: General Help
---

### Post by rebeltaz on 2019-02-16
After following the advice here - [https://ubuntuforums.org/showthread.php?t=2411785&p=13835515#post13835515](https://ubuntuforums.org/showthread.php?t=2411785&p=13835515#post13835515) - in order to obtain the latest/stable version of the nemo file browser (the one in the repository kept crashing randomly), everything went ok until I rebooted. 

When I rebooted the laptop, it kept cycling as if it were stuck in a reboot loop - it would load the BIOS startup screen, go black and reboot. It did this until I turned the computer off and then back on again. Then, it loaded the Ubuntu-colored background but then went to a black screen and threw up this error:

```

error: attempt to read or write outside of disk 'hd0'
Press any key to continue...

```

When I first saw it, well... I did what it said and pressed a key. After a minute, it finally loaded Ubuntu and everything seemed ok. I rebooted again, just to see what was what and this time, I was going to take a picture of the screen. While I was getting my camera, the computer went ahead and booted past that without my having to press any key.

I did a search on that error and it seems to be a grub issue, but since I am not well verse in grub issues, I don't want to screw it up worse by not knowing what I am doing. Any idea what went wrong and how to fix it? I didn't know if I should try tghe "if anything goes wrong" suggestion on that thread for this issue or not. I have not received a response to that thread for this error, so I figured I'd try the general population. Thanks.

---

### Post by sudodus on 2019-02-16
If you cannot reproduce the error, I think you need not worry about it.

If you wish to check anyway, you can

- check the [S.M.A.R.T. status](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors-what-should-i-do-now/972983#972983) of the system disk, 

- check the [file system](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors-what-should-i-do-now/972983#972983) (scroll down to 'Run fsck on an ext4 file system'), when booted from another drive, for example a live drive with Ubuntu.

- check [RAM (a long check overnight)](https://askubuntu.com/questions/917961/can-i-boot-memtest86-if-im-using-uefi/917998#917998) with memtest86+ from the boot menu (in BIOS mode) or the separate program memtest86 in UEFI mode.

---

### Post by rebeltaz on 2019-02-16
I'm sorry... I should have been more clear. This wasn't a one time thing. That wouldn't have bothered me so much. This is an ongoing issue. It occurs every time I turn on my laptop. I can still use it, it just adds a few minutes wait time to boot up and, besides that... I hate unexplained errors. 

I will try all of those tests, but if the fact that it is recurring changes anything, I'd be appreciative of any further advice you might have. Thanks.

---

### Post by sudodus on 2019-02-16
Sorry for misunderstanding. Now I understand why you are bothered.

- It is still (and even more) meaningful to check those 3 things (of my previous post).

- You can also run the following command lines and show the result rendered as 'code',

```

sudo lsblk -f
sudo lsblk -m

sudo parted -ls

df -h

```

[hr][/hr]
You can also do the following from the grub menu:

- Press 'e' and get to the grub prompt
- run the command **ls**
- write down the result

and compare it to the content of the file **/boot/grub/grub.cfg**

Is **grub.cfg** pointing to a partition, that does not exist,or to another drive than the intended?

---

### Post by rebeltaz on 2019-02-16
I will do the memory test and the disk test tonight and let you know those results tomorrow, but in the meantime, these are the results of the other tests so far:


> **sudodus] - check the S.M.A.R.T. status of the system disk[/quote]
Disks reports - Disk is OK, one bad sector (41° C / 106° F)

[QUOTE=sudodus]sudo lsblk -f[/quote]
```

NAME   FSTYPE  LABEL UUID                                 MOUNTPOINT
loop0  squashf                                            /snap/gtk-common-theme
loop1  squashf                                            /snap/gnome-logs/45
loop2  squashf                                            /snap/gtk-common-theme
loop3  squashf                                            /snap/gnome-characters
loop4  squashf                                            /snap/gnome-system-mon
loop5  squashf                                            /snap/gnome-characters
loop6  squashf                                            /snap/gnome-calculator
loop7  squashf                                            /snap/gnome-system-mon
loop8  squashf                                            /snap/core/6259
loop9  squashf                                            /snap/gnome-system-mon
loop10 squashf                                            /snap/gnome-logs/43
loop11 squashf                                            /snap/core/6405
loop12 squashf                                            /snap/gnome-3-26-1604/
loop13 squashf                                            /snap/gtk-common-theme
loop14 squashf                                            /snap/gnome-calculator
loop15 squashf                                            /snap/gnome-calculator
loop16 squashf                                            /snap/core/6350
loop17 squashf                                            /snap/gnome-3-26-1604/
loop18 squashf                                            /snap/gnome-logs/40
loop19 squashf                                            /snap/gnome-3-26-1604/
loop20 squashf                                            /snap/gnome-characters
sda                                                       
&#9492 said:**
> sudo lsblk -m
```

NAME     SIZE OWNER GROUP MODE
loop0   34.8M root  disk  brw-rw----
loop1   14.5M root  disk  brw-rw----
loop2   34.2M root  disk  brw-rw----
loop3     13M root  disk  brw-rw----
loop4    3.7M root  disk  brw-rw----
loop5     13M root  disk  brw-rw----
loop6    2.2M root  disk  brw-rw----
loop7    3.7M root  disk  brw-rw----
loop8   91.1M root  disk  brw-rw----
loop9    3.7M root  disk  brw-rw----
loop10  14.5M root  disk  brw-rw----
loop11    91M root  disk  brw-rw----
loop12 140.7M root  disk  brw-rw----
loop13  34.6M root  disk  brw-rw----
loop14   2.3M root  disk  brw-rw----
loop15   2.3M root  disk  brw-rw----
loop16    91M root  disk  brw-rw----
loop17 140.7M root  disk  brw-rw----
loop18  14.5M root  disk  brw-rw----
loop19 140.9M root  disk  brw-rw----
loop20    13M root  disk  brw-rw----
sda    465.8G root  disk  brw-rw----
&#9492;&#9472;sda1 465.8G root  disk  brw-rw----
sr0     1024M root  cdrom brw-rw----

```


[QUOTE=sudodus]sudo parted -ls[/quote]
```

Model: ATA ST9500420AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ext4         boot

```


[QUOTE=sudodus]df -h[/quote]
```

Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           375M  1.8M  373M   1% /run
/dev/sda1       458G  249G  186G  58% /
tmpfs           1.9G   47M  1.8G   3% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop2       35M   35M     0 100% /snap/gtk-common-themes/808
/dev/loop4      3.8M  3.8M     0 100% /snap/gnome-system-monitor/54
/dev/loop5       13M   13M     0 100% /snap/gnome-characters/139
/dev/loop6      2.3M  2.3M     0 100% /snap/gnome-calculator/222
/dev/loop7      3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop9      3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop13      35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop11      91M   91M     0 100% /snap/core/6405
/dev/loop1       15M   15M     0 100% /snap/gnome-logs/45
/dev/loop3       13M   13M     0 100% /snap/gnome-characters/117
/dev/loop10      15M   15M     0 100% /snap/gnome-logs/43
/dev/loop14     2.3M  2.3M     0 100% /snap/gnome-calculator/238
/dev/loop15     2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop18      15M   15M     0 100% /snap/gnome-logs/40
/dev/loop19     141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop20      13M   13M     0 100% /snap/gnome-characters/124
/dev/loop0       35M   35M     0 100% /snap/gtk-common-themes/1122
/dev/loop12     141M  141M     0 100% /snap/gnome-3-26-1604/78
/dev/loop16      91M   91M     0 100% /snap/core/6350
/dev/loop8       92M   92M     0 100% /snap/core/6259
/dev/loop17     141M  141M     0 100% /snap/gnome-3-26-1604/74
tmpfs           375M  112K  375M   1% /run/user/1000

```

---

### Post by sudodus on 2019-02-17
The S.M.A.R.T. status looks good. The root partition **/dev/sda1** looks like it should.

It will be interesting to see the result of the next tasks (checking and if necessary repairing the file system, checking the RAM and comparing **ls** in **grub** with **grub.cfg**).

---

### Post by rebeltaz on 2019-02-17
hmmm... so the file system check reported that the supberblock was bad:

```

e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a dos partition table in /dev/sda

```

I have had superblock issues before on external backup drives, so I know about mke2fs to find the alternative superblock magic numbers (why does working in linux feel like I'm on a quest from King Arthur and the Knights of the Roundtable?) but when I ran that command, it too complained that a dos partition was found - was I sure that I wanted to continue. Before I go trying to "correct" something incorrectly and destroy data, I figured I'd get your input first.

---

### Post by rbmorse on 2019-02-17
My advice is to backup any irreplaceable data onto another storage device before you do anything else if you're not already doing so.

---

### Post by rebeltaz on 2019-02-17
I do keep backups and I am now backing up anything not backed up since the last backup,but... after I do that, just try to recover with the alternative superblocks?

---

### Post by Bashing-om on 2019-02-17
rebeltaz; Hello -

slickymaster has a most excellent guide to spare of that superblock:
[http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by sudodus on 2019-02-18
The output makes it seem like you try on the whole drive

```

sudo e2fsck -f /dev/sda

```

but you should point the command to the **partition** with an ext4 file system

```

sudo e2fsck -f /dev/sda1

```

Notice the trailing '1' in the command line.

---

### Post by rebeltaz on 2019-02-21
> **sudodus said:**
> The output makes it seem like you try on the whole drive

```

sudo e2fsck -f /dev/sda

```

but you should point the command to the **partition** with an ext4 file system

```

sudo e2fsck -f /dev/sda1

```

Notice the trailing '1' in the command line.

That's what I was doing. When I ran it on the partition, it came back with no errors. I finally got it fixed. Going on your grub suggestion, I ran boot-repair on it. Doing it with the default settings, didn't fix anything, but when I ran it and told it to purge grub completely and reinstall it... that seems to have done the trick. Thank you!

---

### Post by sudodus on 2019-02-22
Congratulations :-) I'm glad that you found a solution and thanks for sharing it. It can be useful for other people.

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

