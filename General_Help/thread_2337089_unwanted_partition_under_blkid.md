---
title: "unwanted partition under blkid"
date: 2016-09-14
forum: General Help
---

### Post by digitalquake on 2016-09-14
Hello all I'm new.

I was trying to create a USB boot with centOS from my Ubuntu 14.04 and I wrote the *.iso file to a partition of the usb instead of the top level. 

dd if=CentOS-6.5-x86_64-bin-DVD1.iso of=/dev/sdd1 instead of  dd if=CentOS-6.5-x86_64-bin-DVD1.iso of=/dev/sdd

Now I have 2x partitions that I can't unmount and I don't know what to do.

sudo blkid
```
/dev/sdb1: LABEL="Raid1" UUID="76c46b07-65d8-4be5-aef8-da19ea089487" TYPE="ext4" 
/dev/sdc1: LABEL="Raid2" UUID="dc69ebeb-339c-4bd0-9d4a-e0b83ddc825b" TYPE="ext4" 
/dev/sda1: UUID="d85c136c-c30b-4ef7-9c17-8ffb6fe2951a" TYPE="ext2" 
/dev/sda5: UUID="MAEV5H-hQQw-fjdj-4KJn-tS9v-1WBv-mGYWe1" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="d4a2dd55-2950-4b40-b4a4-8897f33c2741" TYPE="ext4" 
/dev/mapper/ubuntu--vg-swap_1: UUID="1bce63fd-3f67-489f-a3f9-d5fcfe6ac62e" TYPE="ext4" LABEL="delete1" 
```

the latter two are there by mistake and I can't unmount or remove them with "Disks"
I think they automounted when I tried to view the usb from the dock.
Can someone please tell me the best way to get rid of them?

Thank you

---

### Post by steeldriver on 2016-09-14
Hello and welcome to the forums 

[FONT=courier new]/dev/mapper/ubuntu--vg-root[/FONT] and [FONT=courier new]/dev/mapper/ubuntu--vg-swap_1[/FONT] look like the root and swap of your running Ubuntu system - what make you think that they are anything to do with the CentOS ISO (or are "unwanted")

---

### Post by digitalquake on 2016-09-14
I think that they have never been there (and in the ubuntu disk utilty as well) 
Am I misunderstanding something? My main SSD is 120GB and it's shown as partitioned with blocks under /dev/sda. While those two are under "Other Devices" and total of them is 85+34=119GB

[http://pasteboard.co/33DWTDu89.png](http://pasteboard.co/33DWTDu89.png)

After I compiled the USB multiple partitions started to mounting, even when I was unplugging the pendrive, and I thought those were duplicates.

EDIT
also the swap is mounted under /media/usr/1bce63fd-3f67-489f-a3f9-d5fcfe6ac62e

---

### Post by sudodus on 2016-09-14
Welcome to the Ubuntu Forums :_)

Please post the output of the following commands,

```
df -h

sudo lsblk -fm
```

It will help us help you.

---

### Post by digitalquake on 2016-09-15
Hi sudodus

df -h
```

Filesystem                     Size  Used Avail Use% Mounted on
udev                            16G  604M   16G   4% /dev
tmpfs                          3.2G  1.9M  3.2G   1% /run
/dev/dm-0                       78G   38G   36G  52% /
none                           4.0K     0  4.0K   0% /sys/fs/cgroup
none                           5.0M     0  5.0M   0% /run/lock
none                            16G  944K   16G   1% /run/shm
none                           100M   92K  100M   1% /run/user
/dev/sda1                      236M   73M  152M  33% /boot
/dev/sdb1                       11T  8.3T  2.0T  81% /mnt/sdb1
/dev/sdc1                      917G  632G  238G  73% /mnt/sdc1
//10.11.7.10/Promise Pegasus/   14T   13T  1.5T  90% /media/share
//10.11.7.10/macintosh_hd_tm/  932G  146G  786G  16% /media/okayslave
/dev/mapper/ubuntu--vg-swap_1   32G   48M   30G   1% /media/andrea/1bce63fd-3f67-489f-a3f9-d5fcfe6ac62e

```


sudo lsblk -fm

```

NAME                          FSTYPE      LABEL     MOUNTPOINT                                     NAME                           SIZE OWNER GROUP MODE
sda                                                                                               sda                          111.3G root  disk  brw-rw----
&#9500;&#9472;sda1                        ext2                  /boot                                          &#9500;&#9472;sda1                         243M root  disk  brw-rw----
&#9500;&#9472;sda2                                                                                            &#9500;&#9472;sda2                           1K root  disk  brw-rw----
&#9492;&#9472;sda5                        LVM2_member                                                          &#9492;&#9472;sda5                         111G root  disk  brw-rw----
   &#9500;&#9472;ubuntu--vg-root (dm-0)   ext4                   /                                               &#9500;&#9472;ubuntu--vg-root  (dm-0)    79.1G root  disk  brw-rw----
  &#9492;&#9472;ubuntu--vg-swap_1 (dm-1)  ext4                  /media/andrea/1bce63fd-3f67-489f-a3f9-d5fcfe6    &#9492;&#9472;ubuntu--vg-swap_1 (dm-1)  31.9G root  disk  brw-rw----
sdb                                                                                               sdb                           10.9T root  disk  brw-rw----
&#9492;&#9472;sdb1                        ext4        Raid1 /mnt/sdb1                                      &#9492;&#9472;sdb1                        10.9T root  disk  brw-rw----
sdc                                                                                               sdc                            931G root  disk  brw-rw----
&#9492;&#9472;sdc1                        ext4        Raid2 /mnt/sdc1                                      &#9492;&#9472;sdc1                         931G root  disk  brw-rw----


```

---

### Post by sudodus on 2016-09-15
Your system is booted from /dev/sda1, and then it is using LVM with the root partition /dev/ubuntu--vg-root (dm-0) and the swap partition /dev/ubuntu--vg-swap_1 (dm-1).

Obviously you installed Ubuntu with LVM, which is an option in the installer, at the partitioning page. Those partitions have nothing to do with your attempt to install Centos, and you should not try to get rid of them :-)

-o-

You can try again with ***dd***, but in order to be (and feel) safer, when you create USB boot drives, you can use ***mkusb***, which 'wraps a safety belt' around dd. See this link,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by digitalquake on 2016-09-15
Thanks sudodus, I was close to drop a bomb :/

---

### Post by sudodus on 2016-09-15
You are welcome :-)

If you feel that the problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by digitalquake on 2016-09-26
Hi

I thought this was solved but, after a reboot, I now have a mounted 34GB partition showing up in the dekstop.
Am I missing something?

---

### Post by sudodus on 2016-09-26
Please post the output of your current system again from

```
sudo lsblk -fm
```

and attach a screenshot of your desktop: press the 'Go Advanced' button, and then the 'Manage Attachment' button and use the pop up window to select and attach the screenshot flle to a reply.

This way it will be easier to identify what you see in the desktop (the mounted 34GB partition). Maybe it is the swap partition, which has an ext4 file system. It should have no file system, but be created as 'linux swap'. But without more information I can only guess.

---

### Post by digitalquake on 2016-09-26
Hi

I thought this was solved but, after a reboot, I now have a mounted 34GB partition showing up in the dekstop.
Am I missing something?

---

### Post by sudodus on 2016-09-26
You repeated post #9 as post #11.

It is hard for me to identify what you see on your desktop, so please give me the information that I asked for in post #10. Otherwise I can only guess.

I can add a question here: Is the following line still displayed by ***lsblk -fm***, and in that case, why do you use 31.9 GiB for swap? It seems too much drive space for that purpose. Or is it used for something else (not swap)? Why ext4 and swap?

```
&#9492;&#9472;ubuntu--vg-swap_1 (dm-1)  ext4        /media/andrea/1bce63fd-3f67-489f-a3f9-d5fcfe6    &#9492;&#9472;ubuntu--vg-swap_1 (dm-1)  [COLOR="#cc0000"]31.9G[/COLOR] root  disk  brw-rw----
```

---

### Post by digitalquake on 2016-09-26
Hi

First
sorry if I'm duplicating posts my browser got stuck while posting a couple of times.

second

```

andrea@okaybrain:~$ lsblk -fm
NAME                         FSTYPE LABEL MOUNTPOINT                                         NAME                           SIZE OWNER GROUP MODE
sda                                                                                          sda                          111.3G root  disk  brw-rw----
&#9500;&#9472;sda1                                    /boot                                              &#9500;&#9472;sda1                         243M root  disk  brw-rw----
&#9500;&#9472;sda2                                                                                       &#9500;&#9472;sda2                           1K root  disk  brw-rw----
&#9492;&#9472;sda5                                                                                       &#9492;&#9472;sda5                         111G root  disk  brw-rw----
  &#9500;&#9472;ubuntu--vg-root (dm-0)                /                                                    &#9500;&#9472;ubuntu--vg-root (dm-0)    79.1G root  disk  brw-rw----
  &#9492;&#9472;ubuntu--vg-swap_1 (dm-1)              /media/andrea/1bce63fd-3f67-489f-a3f9-d5fcfe6ac62e   &#9492;&#9472;ubuntu--vg-swap_1 (dm-1)  31.9G root  disk  brw-rw----
sdb                                                                                          sdb                           10.9T root  disk  brw-rw----
&#9492;&#9472;sdb1                                    /mnt/sdb1                                          &#9492;&#9472;sdb1                        10.9T root  disk  brw-rw----
sdc                                                                                          sdc                            931G root  disk  brw-rw----
&#9492;&#9472;sdc1                                    /mnt/sdc1                                          &#9492;&#9472;sdc1                         931G root  disk  brw-rw----

```

I've inherited the system I'm working with from a previous technician so I'm not sure why there's this setup.

 
here the screenshot

---

### Post by sudodus on 2016-09-26
The partition table is very unusual.

Are there things installed in this system, that you want to or must keep?

- If yes, I suggest that you ask the technician what is the reason for this unusual partition table and after that decide what to do with it.

- If no, I suggest that you start with a fresh installation of a current version of Ubuntu. You can try live with the version ***14.04.1 LTS*** (as seems to be installed) and the newer ***16.04.1 LTS***. See this link:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

I suggest that you let Ubuntu use the whole drive (and it will create a big root partition and a much smaller swap partition (that will be correctly formatted as swap).

---

### Post by digitalquake on 2016-09-27
I think I'll have to do a fresh-install because the system has too many holes at the moment. It's just annoying :)

---

### Post by sudodus on 2016-09-27
Whatever your result, please tell us.

Good luck :-)

---

