---
title: "How to change auto-mount point of SD Card"
date: 2018-10-31
forum: General Help
---

### Post by migillope on 2018-10-31
Ubuntu 16.04.5

Ages ago, I found a page (not on the forums) that gave a how to on auto mounting an sd-card with this crouton chromebook ubuntu tragedy. I think it wrote a script or something, I'm not sure, it was a long time ago. I ran 'sudo find / <something>' replacing <something> with anything I could think of, no dice.

The SD Card auto-mounts to '/media/removable/SD Card' but I need it to mount to '/media/removable/sdcard' because a program cannot run with a space in its path.

Every time I boot, I have to issue the commands:
sudo umount /dev/sda1
sudo mv '/media/removable/SD Card' '/media/removable/sdcard'
sudo mount /dev/sda1 /media/removable/sdcard

I would like this to be done on boot. I can't add it to the xfce4 auto-start thing because of permissions. I tried writing a script to do this for me, but obviously I didn't know what I was doing because it broke everything and I had to drop into emergency shell.

/etc/fstab is empty, and since I am running this on a chromebook, I have a million nonsense partitions so I'd prefer not to make an fstab. 

Thank you :)

---

### Post by ajgreeny on 2018-10-31
Use gparted or command line tune2fs to give the partition a label of **sdcard** and it will then automount to **/media/removable/sdcard** exactly as you wish, assuming you have username **removable**.

If your username is not removable we will need to know more about your system, the users on it, and the partitions used.

---

### Post by migillope on 2018-10-31
My username is not removable.

The only user is migillope, here is lsblk:

```

NAME           MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda              8:0    1 29.7G  0 disk 
`-sda1           8:1    1 29.7G  0 part /var/host/media/removable/SD Card
loop0            7:0    0  3.1G  0 loop 
`-encstateful  253:1    0  3.1G  0 dm   /var/host/timezone
loop1            7:1    0 14.8M  1 loop 
`-466BF32BFE2A772844EF014A6A6D641E519F02997CC06DDC14EB7B9278AEC3D2
               253:2    0 14.6M  1 dm   
zram0          252:0    0  5.5G  0 disk [SWAP]
mmcblk0rpmb    179:48   0    4M  0 disk 
mmcblk0boot0   179:16   0    4M  1 disk 
mmcblk0boot1   179:32   0    4M  1 disk 
mmcblk0        179:0    0 14.7G  0 disk 
|-mmcblk0p1    179:1    0 10.5G  0 part /home/migillope/Downloads
|-mmcblk0p2    179:2    0   16M  0 part 
|-mmcblk0p3    179:3    0    2G  0 part 
| `-vroot      253:0    0  1.7G  1 dm   /lib/modules/4.4.141-14567-g26df737f0737
|-mmcblk0p4    179:4    0   16M  0 part 
|-mmcblk0p5    179:5    0    2G  0 part 
|-mmcblk0p6    179:6    0  512B  0 part 
|-mmcblk0p7    179:7    0  512B  0 part 
|-mmcblk0p8    179:8    0   16M  0 part 
|-mmcblk0p9    179:9    0  512B  0 part 
|-mmcblk0p10   179:10   0  512B  0 part 
|-mmcblk0p11   179:11   0    8M  0 part 
`-mmcblk0p12   179:12   0   16M  0 part 

```

---

### Post by ajgreeny on 2018-11-01
It would therefore seem likely that the sd card is mounted at boot from an entry for it in /etc/fstab.

Please show us the output of ```
cat /etc/fstab
``` and we can try to get it to mount as you want.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by migillope on 2018-11-01
I mentioned this in the OP, /etc/fstab is empty. There was a comment about it being empty (no other useful information), but I deleted it when trying to fix the issue.

---

### Post by ajgreeny on 2018-11-02
> **migillope said:**
> I mentioned this in the OP, /etc/fstab is empty. There was a comment about it being empty (no other useful information), but I deleted it when trying to fix the issue.
In that case I'm afraid this problem is completely outside of my knowledge base and I will have to leave it to others to help..

---

### Post by HermanAB on 2018-11-02
Note that if you give a removable device a Volume Name, then it will always mount with that name.  So you don't need to change any heavy configuration in the system, just run the disk utility and give the SD card a Volume Name with no space in that name.

---

