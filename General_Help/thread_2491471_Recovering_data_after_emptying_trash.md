---
title: "Recovering data after emptying trash"
date: 2023-10-10
forum: General Help
---

### Post by nonetheless on 2023-10-10
I saw something unusual on my desktop. I deleted it and never saw  that I emptied my whole laptop drive, further I emptied the trash  moments later. When I noticed it, I tried to recover using Testdisk,  with help of this site: [https://www.makeuseof.com/how-to-recover-lost-damaged-data-with-testdisk/](https://www.makeuseof.com/how-to-recover-lost-damaged-data-with-testdisk/)

 There was no partition in my disk. I started testdisk with creating logfile.`

 ```
Select a media (use Arrow keys, then press Enter):
>Disk /dev/sda - 1000 GB / 931 GiB - TOSHIBA MQ01ABD100
 Disk /dev/sdb - 1000 GB / 931 GiB - Seagate Portable
 Disk /dev/mapper/ubuntu--vg-root - 995 GB / 927 GiB - TOSHIBA MQ01ABD100
 Disk /dev/mapper/ubuntu--vg-swap_1 - 4064 MB / 3876 MiB - TOSHIBA MQ01ABD100
 Disk /dev/dm-0 - 995 GB / 927 GiB - TOSHIBA MQ01ABD100
 Disk /dev/dm-1 - 4064 MB / 3876 MiB - TOSHIBA MQ01ABD100
 Disk /dev/loop0 - 66 MB / 63 MiB (RO)
 Disk /dev/loop1 - 521 MB / 496 MiB (RO)
 Disk /dev/loop10 - 470 MB / 448 MiB (RO)
 Disk /dev/loop11 - 524 KB / 512 KiB (RO)
>[Previous]  [  Next  ]  [Proceed ]  [  Quit  ]

``` I chose >Disk /dev/sda - 1000 GB / 931 GiB - TOSHIBA MQ01ABD100
 I got `
```
Disk /dev/sda - 1000 GB / 931 GiB - TOSHIBA MQ01ABD100
```
Please select the partition table type, press Enter when done.
```
>[Intel  ] Intel/PC partition
 [EFI GPT] EFI GPT partition map (Mac i386, some x86_64...)
 [Humax  ] Humax partition table
 [Mac    ] Apple partition map (legacy)
 [None   ] Non partitioned media
 [Sun    ] Sun Solaris partition
 [XBox   ] XBox partition
 [Return ] Return to disk selection


```
` I chose Intel  and got `

```
Disk /dev/sda - 1000 GB / 931 GiB - TOSHIBA MQ01ABD100
     CHS 121601 255 63 - sector size=512
 [ Analyse  ] Analyse current partition structure and search for lost partitions
>[ Advanced ] Filesystem Utils
 [ Geometry ] Change disk geometry
 [ Options  ] Modify options
 [ MBR Code ] Write TestDisk MBR code to first sector
 [ Delete   ] Delete all data in the partition table
 [ Quit     ] Return to disk selection


`
``` On Analyse I got `

```
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors
 1 * Linux                    0  32 33    62  53 55     997376
 2 E extended                62  86 23 121601  57 56 1952522242
 5 L Linux LVM               62  86 25 121601  57 56 1952522240


```
 It was dead-end, it asked nothing to do there. So I  got to the previous screen and chose **Advaned**
 It gave me `
```
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition                  Start        End    Size in sectors
> 1 * Linux                    0  32 33    62  53 55     997376
  2 E extended                62  86 23 121601  57 56 1952522242
  5 L Linux LVM               62  86 25 121601  57 56 1952522240

 [  Type  ]  [Superblock]  [Undelete] >[Image Creation]  [  Quit  ]


```' On choosing the 2nd part > Extended  I got only these option: `
```
Partition                  Start        End    Size in sectors
  1 * Linux                    0  32 33    62  53 55     997376
> 2 E extended                62  86 23 121601  57 56 1952522242
  5 L Linux LVM               62  86 25 121601  57 56 1952522240


 [  Type  ] >[Image Creation]  [  Quit  ]



```` It did not show which files to recover, so I selected to create image of the partition, which gave me `
```
Please select where to store the file image.dd (999691 MB), an image of the
partition
Keys: **Arrow** keys to select another directory
      **C** when the destination is correct
      **Q** to quit
Directory /home/alpha
>drwxr-xr-x  1000  1000      4096 10-Oct-2023 15:49 .
 drwxr-xr-x     0     0      4096 28-Aug-2022 23:19 ..
 drwxr-xr-x  1000  1000      4096 28-Jun-2023 18:41 Documents
 drwxr-xr-x  1000  1000     12288  7-Oct-2023 15:22 Downloads
 drwxrwxr-x  1000  1000      4096 17-Sep-2023 21:30 Eternal hard disk
 drwxr-xr-x  1000  1000      4096 28-Aug-2022 23:30 Music
 drwxrwxr-x  1000  1000      4096 29-Sep-2023 20:43 Para
 drwxr-xr-x  1000  1000      4096 28-Aug-2022 23:30 Videos
 drwx------  1000  1000      4096  5-Aug-2023 23:18 snap
 -rw-r--r--  1000  1000 1037917997 12-Dec-2022 08:32 Heat1995[13gb].mp4
 -rw-rw-r--  1000  1000     66719 10-Oct-2023 15:49 Screenshot from 2023-10-10 1
 -rw-r--r--  1000  1000 1751858879  6-Oct-2023 22:11 The.Drop.2014.m720p.rar
 -rw-rw-r--  1000  1000       267  6-Oct-2023 22:11 The.Drop.2014.m720p.rar.aria
 -rw-r--r--  1000  1000   1187407 20-Oct-2022 10:07 hrmd2022654.pdf
 -rw-rw-r--  1000  1000      4942 10-Oct-2023 17:07 testdisk.log

```` This is where I am facing two problems:
 
[LIST=1]
[*]It is said not to copy files to the same location where it  belonged, so I wanted to copy the files to an external hard drive. My  external hard drive it connected to my laptop but the list doesn't show  it. So I cannot  choose it.

[*]I don't have an empty 1TB External HDD ready in my hands to copy that image.
[/LIST]
 

 Note: I did not use the drive to copy other files, so nothing is overwritten. I just downloaded Testdisk.

So what to to?

---

### Post by oldfred on 2023-10-10
Since LVM, did you also use full drive encryption? That is intended to prevent anyone from recovering data.
If LVM still valid, you would have to mount it & decrypt it to see into it.

Otherwise, then only recourse is to restore from your normal backups.

---

### Post by nonetheless on 2023-10-10
No I didn't have any encryption on the drive.. and I don't have backups either..

So, It's an impossible task?

---

### Post by oldfred on 2023-10-10
I do not know LVM.
Can you mount it before using testdisk? So testdisk can see the files.
I just do not now if testdisk works with LVM?

Otherwise if not encrypted, you can use testdisk's Photorec. Very slow, requires another drive and only recovers files by file extension.
I used it once on a smaller drive. Took overnight to run. And recovered many copies of some text files I had saved many times. Had to do a lot of sorting & comparing, took weeks to resolve and not sure if final version of some text files was most current or not. Learned to have better backups.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by TheFu on 2023-10-10
Try to restore  /dev/mapper/ubuntu--vg-root.  That's the place where the OS is located on your setup.  You are using LVM, which means someone selected that at install-time.

It really would be best to have backups. They are 100x easier to restore than any data recovery technique and since an external 2-4TB HDD is only $30-$50, there is little excuse not to have plenty of backup versions.

When you try to restore the data, you'll need another, unused, storage area to receive the files.  The restored files will not have the same name. They will be f{random}.{ext}, so good luck putting multiple-part files back together.  Also, these restore tools will often find 2-5 versions of the same file, so you'll need to figure out which is the version you actually want.

It really would be best to have backups. to restore using.

---

### Post by coffeecat on 2023-10-10
The *Assistive Technology & Accessibility* sub-forum where you posted this thread is for, "discussions about software that enables or helps people with various disabilities or impairments (mobility, visual, hearing, cognitive, etc.) to use the computer."

The *General Help* sub-forum is a better fit for your particular problem, so I've moved this thread there. Good luck.

---

