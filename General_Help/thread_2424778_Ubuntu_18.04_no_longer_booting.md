---
title: "Ubuntu 18.04 no longer booting"
date: 2019-08-14
forum: General Help
---

### Post by rudy-258 on 2019-08-14
Hi,

I am running a dual boot with Windows 10 and Windows 10 can boot perfectly fine. 

Whenever I try booting into Ubuntu, I get to the screen with the Ubuntu logo and it just starts flickering. This goes on forever. Until yesterday, a restart usually fixed the problem and I was able to boot up. That is no longer the case. 

I realized that my Ubuntu partition was 100% full, so I used a live USB to use Gparted and give it more space, however, I am still having the same problem. 

Booting into recovery mode and then selecting "resume boot" is also no longer working. I just get to a black screen with a blinking cursor on the top left corner. I can access the root shell from the recovery mode though. I tried running the repair packages option, but that failed too. 

I will gladly provide more if information that is required. 

Any help would be greatly appreciated!

---

### Post by TheFu on 2019-08-14
After increasing the partition size, did you also expand the file system to that larger size?

---

### Post by rudy-258 on 2019-08-14
As far as I understand, I think so. See attached image. 

sda5 is the actual Ubuntu partition. I resized both sda2 and sda5 from 20 GB originally, to 117 GB, which I freed up from the windows partition.

 [ATTACH=CONFIG]283793[/ATTACH]

---

### Post by TheFu on 2019-08-14
I can't tell what that image shows.  Please post:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo parted -l

```using code tags like I did for the commands.

Text is always preferred.

---

### Post by rudy-258 on 2019-08-14
Thanks for your reply. 

Here is the output:

```

ubuntu@ubuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type     Size  Used Avail Use% Mounted on
/dev/sdb1      vfat      29G  1.9G   27G   7% /cdrom
/cow           overlay  3.9G  429M  3.5G  11% /
/dev/sda5      ext4     116G   18G   93G  16% /media/ubuntu/064ca4a6-dbbe-4a65-ae10-a00b186072a5


```

```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  366GB  366GB   primary   ntfs            boot
 2      366GB   492GB  126GB   extended
 5      366GB   492GB  126GB   logical   ext4
 3      492GB   493GB  1000MB  primary   linux-swap(v1)
 4      493GB   500GB  7247MB  primary   ext4


Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 30.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  30.8GB  30.8GB  primary  fat32        boot, lba



```

---

### Post by TheFu on 2019-08-14
And for sda4, the **df** (fixed mistake of 'du').

```

Number  Start   End    Size    Type      File system     Flags
 5      366GB   492GB  126GB   logical   ext4
 4      493GB   500GB  7247MB  primary   ext4
```

Looks like sda4 is 7G.  If that is where / is mounted, you'll need to remove some files there that aren't harmful.  If / or /var/ gets full, Unix OSes don't like it.

---

### Post by rudy-258 on 2019-08-14
I had SDA5 mounted since I was recovering data. Now I tried running the command again after unmounting it, here is the output:

```

ubuntu@ubuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type     Size  Used Avail Use% Mounted on
/dev/sdb1      vfat      29G  1.9G   27G   7% /cdrom
/cow           overlay  3.9G  430M  3.5G  11% /

```

```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  366GB  366GB   primary   ntfs            boot
 2      366GB   492GB  126GB   extended
 5      366GB   492GB  126GB   logical   ext4
 3      492GB   493GB  1000MB  primary   linux-swap(v1)
 4      493GB   500GB  7247MB  primary   ext4


Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 30.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  30.8GB  30.8GB  primary  fat32        boot, lba



```

This is all that's being shown now. The Gparted GUI still shows the other devices, but not in the terminal.

---

### Post by TheFu on 2019-08-14
**df** only works when mounted. Sorry about the "du" above. That is a mistake.

---

### Post by rudy-258 on 2019-08-14
Is sda4 part of my Ubuntu installation? Also, why isn't 7 GB there not enough? It does have 6.53 GB free.

---

### Post by TheFu on 2019-08-14
> **rudy-258 said:**
> Is sda4 part of my Ubuntu installation? Also, why isn't 7 GB there not enough? It does have 6.53 GB free.

I don't know. Cannot tell from the data provided.   Looks like my hope of solving this with a quick answer isn't going to work. We need much more data and some other experts.

 Boot into the Ubuntu Live environment, install boot-repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) , run it, but **don't let it try to fix anything**. It can break systems, now that so many different configurations are possible.  Use the "Create BootInfo" button (whatever it is called, center bottom of the screen), and post the URL that it creates back here.  That URL will contain lots of information about the boot and storage config of the system.

---

### Post by &amp;wP*!) on 2019-08-14
> **rudy-258 said:**
> Is sda4 part of my Ubuntu installation? Also, why isn't 7 GB there not enough? It does have 6.53 GB free.
Can you type
```
lsblk -o NAME,TYPE,SIZE,MOUNTPOINT
```
.. and copy-paste what the command returns?

---

### Post by rudy-258 on 2019-08-14
```

ubuntu@ubuntu:~$ lsblk -o NAME,TYPE,SIZE,MOUNTPOINT
NAME   TYPE   SIZE MOUNTPOINT
loop0  loop   1.7G /rofs
loop1  loop  86.6M /snap/core/4486
loop2  loop   140M /snap/gnome-3-26-1604/59
loop3  loop   1.6M /snap/gnome-calculator/154
loop4  loop  12.2M /snap/gnome-characters/69
loop5  loop    21M /snap/gnome-logs/25
loop6  loop   3.3M /snap/gnome-system-monitor/36
sda    disk 465.8G 
&#9500;&#9472;sda1 part   341G 
&#9500;&#9472;sda3 part   954M [SWAP]
&#9500;&#9472;sda4 part   6.8G 
&#9492;&#9472;sda5 part 117.1G 
sdb    disk  28.7G 
&#9492;&#9472;sdb1 part  28.7G /cdrom


```

And for boot-repair:
[http://paste.ubuntu.com/p/sk3k3ZjXmv/](http://paste.ubuntu.com/p/sk3k3ZjXmv/)

---

### Post by &amp;wP*!) on 2019-08-15
This might not be related to your filesystem/partitioning.

Do you have an Intel graphics driver? You can check it with
```
lshw -c video
```
If it says Intel somewhere, then you can try this:
[LIST=1]
[*]add **i915.enable_psr=0** inside the string (i.e. inside the " " ) in GRUB_CMDLINE_LINUX_DEFAULT of **/etc/default/grub**.
[*]generate GRUB config file with **grub-mkconfig -o /boot/grub/grub.cfg** (if your GRUB file is there).
[*]reboot. 
[*]
[/LIST]
Let us know if this solves your problem. If not, take back all the changes above (remove the string from /etc/default/grub, generate grub file and reboot).
This workaround was fixed in 5.2.8 kernel, which none of the Ubuntu distros have yet. It will come in 19.10 (October 2019)

---

### Post by rudy-258 on 2019-08-15
Thanks for your reply. 

As far as I can see I don't have any Inter drivers running. I have both an AMD CPU and GPU. 

Since I ran the command in the root shell of the recovery mode, I can't copy and paste the output, but here are some relevant parts of what it says:

```

*-display UNCLAIMED
description: VGA compatible controller
product: Ellesmere [Radeon RX 470/480/570/570x/580/580x]

```

Also, I just tried booting up again and this time I got further than the Ubuntu logo, and I got an error message, which could be releavnt (It was on the screen with the green OK marks).

This is what the message said:

```
[ ******* ] (2 of 2) A start job is running for Hold until boot process finishes up (54s / no limit) 
```

This was just there forever and nothing happened. 

I googled the error message and it does seem to be related to having no more free disc space. There were many different suggested fixes, but since I am a beginner user of Linux, I didn't want to try them before posting here, since I don't want to break something. 

Here is an image of the error message and some of the preceeding commands, if that's helpful:
 [ATTACH=CONFIG]283810[/ATTACH]

Let me know if there is anything else I can provide in the meantime that might help.

---

### Post by TheFu on 2019-08-15
Thanks for the bootinfo.  All I see in there are a few non-answers which make me think the disk is either failing or corrupted.
Boot into a live boot environment again, install **smartmontools** then run the tests followed by the reporting.
```

sudo smartctl -t short /dev/sda
# wait 5-10 minutes (the command above should provide an estimated time
sudo smartctl -A /dev/sda | tee /tmp/sda.smart
```

Check out the _raw_ values.  1, 5, 7, 178, 179, 181, 182, 187, 195-199 are the most important.  Not all storage provides all those values.  

If those all look fine, i.e. zero, then I'd just go into recovery mode using the live-boot and reinstall grub to the boot sector of sda.  I don't remember if recovery mode sets up the chroot for you or not.  Basically, you're booted off the ISO, but all programs and pseudo- file systems are from the HDD.   Before you do this, be certain to have anything you can't lose backed up, that includes the Windows side.  It is very possible that Windows will not boot after this process, so have the backup and recovery disk ready.

---

### Post by joris_donders2 on 2019-08-16
First of all : the UUID's of the partitions are overwritten in a wrong way by Gparted . 
So boot in Windows first and use the tools of Windows for setteling on the hard drives all, of them. How ? That is a Windows problem not Ubuntu's. 

Second (flickering splash on boot) 

open a terminal and give: 
```
 sudo nano /etc/default/grub
``` 
and hit enter + give your password

go with the arrow keys to the line that says "quiet splash" 
and edit it to: "quiet splash nomodeset" 
save and close nano 
type in the terminal 
```
sudo update-grub
```

reboot to see that improves anything (on the flickering aspects) 

Try if in case it keeps doing bad stuff, in the same way and order, to leave quiet splash away from the line (delete it) ; update grub and reboot again: now you'll see a bunch of text scrolling by , but see specially if you come to a good working desktop/ 

This is what you'll need to test first before we search an alternative method or way  . succes !

---

### Post by TheFu on 2019-08-16
Thanks for the boot image. HIGHLY useful.  Seems like you have the dreaded "boot loop" - I've never seen this. Did a google:
[https://askubuntu.com/questions/1037922/ubuntu-18-04-hangs-on-booting-with-message-started-user-manager-for-uid-120-on](https://askubuntu.com/questions/1037922/ubuntu-18-04-hangs-on-booting-with-message-started-user-manager-for-uid-120-on)
Seems related to wayland display manager.  I don't use wayland.  Anyway, try the disable wayland in the link above and report back.

If you try something and it doesn't work, we need to know.

---

