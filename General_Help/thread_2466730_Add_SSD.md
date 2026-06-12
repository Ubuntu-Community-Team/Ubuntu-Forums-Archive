---
title: "Add SSD?"
date: 2021-09-04
forum: General Help
---

### Post by natbrowne on 2021-09-04
Hi,
I just got a new 4TB SSD, drive and want to add it to my server (to replace 3 usb HDD's) I have tried to mount it, but its not working - honestly don't even know if I formatted it correctly so I probably need to start from basics again :(
```
[FONT=monospace][COLOR=#000000]**Disk /dev/sda: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors**[/COLOR]
Disk model: Samsung SSD 870  
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disklabel type: gpt 
Disk identifier: 67F9499E-78EA-4006-84A6-5A62909CBB37 
[/FONT]
```
bunch of other entries for the usb HDD's the nvme and something called loop. Can someone guide me to get the 4TB to auto mount to /data or similar, would like it to be NTFS if possible incase I ever need to get the information in windows.

---

### Post by tea for one on 2021-09-04
Your result looks like a truncated output from [COLOR="#0000FF"]fdisk[/COLOR]?

It is generally better to show the command and the result.

Nevertheless, you have a GPT disk yet no partitions.
Did you create any partitions?

Example below showing partitions

```
edited@edited:~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 111.81 GiB, 120034123776 bytes, 234441648 sectors
Disk model: SanDisk SDSSDHII
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8DBD75FA-8EB0-4CA5-AB0D-80B8017810F7

Device      Start       End   Sectors   Size Type
/dev/sda1    2048    999423    997376   487M EFI System
/dev/sda2  999424 234440703 233441280 111.3G Linux filesystem

```

---

### Post by natbrowne on 2021-09-04
So here is the full output:
```
[FONT=monospace][COLOR=#000000]**Disk /dev/loop0: 55.45 MiB, 58134528 bytes, 113544 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 


[COLOR=#000000]**Disk /dev/loop1: 55.45 MiB, 58130432 bytes, 113536 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 


[COLOR=#000000]**Disk /dev/loop2: 70.32 MiB, 73728000 bytes, 144000 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 


[COLOR=#000000]**Disk /dev/loop3: 67.58 MiB, 70848512 bytes, 138376 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 


[COLOR=#000000]**Disk /dev/loop4: 32.3 MiB, 33865728 bytes, 66144 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 


[COLOR=#000000]**Disk /dev/loop5: 32.31 MiB, 33869824 bytes, 66152 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 


[COLOR=#000000]**Disk /dev/nvme0n1: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Disk model: CT1000P5SSD8                             
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disklabel type: gpt 
Disk identifier: C3880D21-8C04-43F8-9B65-6AA18849B443 

[COLOR=#000000]**Device**[/COLOR][COLOR=#000000]         [/COLOR][COLOR=#000000]**  Start**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**       End**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**   Sectors**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]** Size**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Type**[/COLOR][COLOR=#000000] [/COLOR]
/dev/nvme0n1p1    2048    1050623    1048576  512M EFI System 
/dev/nvme0n1p2 1050624 1953521663 1952471040  931G Linux filesystem 


[COLOR=#000000]**Disk /dev/sda: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Disk model: Samsung SSD 870  
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disklabel type: gpt 
Disk identifier: 67F9499E-78EA-4006-84A6-5A62909CBB37 

[COLOR=#000000]**Device**[/COLOR][COLOR=#000000]     [/COLOR][COLOR=#000000]**Start**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**       End**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**   Sectors**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]** Size**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Type**[/COLOR][COLOR=#000000] [/COLOR]
/dev/sda1   2048 7814035455 7814033408  3.7T Linux filesystem 


[COLOR=#000000]**Disk /dev/sdb: 1.84 TiB, 2000365289472 bytes, 3906963456 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Disk model: My Passport 0827 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disklabel type: dos 
Disk identifier: 0xb89703c8 

[COLOR=#000000]**Device**[/COLOR][COLOR=#000000]     [/COLOR][COLOR=#000000]**Boot**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Start**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**       End**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**   Sectors**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]** Size**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Id**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Type**[/COLOR][COLOR=#000000] [/COLOR]
/dev/sdb1        2048 3906963455 3906961408  1.8T  7 HPFS/NTFS/exFAT 


[COLOR=#000000]**Disk /dev/sdd: 931.49 GiB, 1000170586112 bytes, 1953458176 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Disk model: My Passport 0810 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disklabel type: dos 
Disk identifier: 0xc235bf1c 

[COLOR=#000000]**Device**[/COLOR][COLOR=#000000]     [/COLOR][COLOR=#000000]**Boot**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Start**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**       End**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**   Sectors**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**  Size**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Id**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Type**[/COLOR][COLOR=#000000] [/COLOR]
/dev/sdd1        2048 1953458175 1953456128 931.5G  7 HPFS/NTFS/exFAT 


[COLOR=#000000]**Disk /dev/sdc: 1.84 TiB, 2000365289472 bytes, 3906963456 sectors**[/COLOR][COLOR=#000000] [/COLOR]
Disk model: My Passport 25E1 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disklabel type: gpt 
Disk identifier: 526B3D46-91A2-4A1B-9D99-0CAE765C68A8 

[COLOR=#000000]**Device**[/COLOR][COLOR=#000000]     [/COLOR][COLOR=#000000]**Start**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**       End**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**   Sectors**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]** Size**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Type**[/COLOR][COLOR=#000000] [/COLOR]
/dev/sdc1   2048 3906961407 3906959360  1.8T Microsoft basic data


[/FONT]
```

I just want to have the 4TB Samsung, auto mount and be used for media / data, and NTFS since I could want it in a windows PC at some point. Kinda lost now as where to start ? Using Ubuntu server btw, so only terminal.

---

### Post by tea for one on 2021-09-04
```
Disk /dev/sda: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: Samsung SSD 870  
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disklabel type: gpt 
Disk identifier: 67F9499E-78EA-4006-84A6-5A62909CBB37 

DeviceStart       End   Sectors SizeType
/dev/sda1   2048 7814035455 7814033408  3.7T [COLOR="#0000FF"]Linux filesystem[/COLOR] 
```

You mentioned that you wanted to use the Samsung disk in Windows but you have formatted it with a Linux File System?

After you have re-formatted the disk, here is a link for automounting [https://www.techrepublic.com/article/how-to-properly-automount-a-drive-in-ubuntu-linux/](https://www.techrepublic.com/article/how-to-properly-automount-a-drive-in-ubuntu-linux/)

---

### Post by oldfred on 2021-09-04
Do you have a Windows install or Windows repair disk?
You cannot fix NTFS from Linux, so when chkdsk or defrag is required, you will need Windows.

Do you want one large partition?
If media, you may need that, but then bit more difficult to backup as you need another large drive.
I do like to have an ESP & at least a smaller / with install and just a few repair tools on every larger drive. Just for emergency boot. Although I have flash drives for emergency boot also.

---

