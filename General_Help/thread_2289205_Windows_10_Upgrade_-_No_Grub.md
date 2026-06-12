---
title: "Windows 10 Upgrade - No Grub"
date: 2015-08-02
forum: General Help
---

### Post by mci on 2015-08-02
Hi,

I had a dualboot with Windows 7 and Ububtu 14.04. I did an upgrade to Windows 10 yesterday and during the installation there was a reboot and I was booting into grub rescue. Similar Issue like here: [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue)

Well then I downloaded Boot-Repair. I was able to launch Windows 10 and to finish the upgrade process.

But now, I don't have GRUB, and can't access the linux partitions. I am afraid my linux ext4 partition is corrupted.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/loop0: 1 GiB, 1101672448 bytes, 2151704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xd9fa2484

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048    718847    716800  350M  7 HPFS/NTFS/exFAT
/dev/sda2          718848 367652345 366933498  175G  7 HPFS/NTFS/exFAT
/dev/sda3       367652864 368642047    989184  483M 27 Hidden NTFS WinRE
/dev/sda4       368644094 976771071 608126978  290G  5 Extended
/dev/sda5       951822336 976771071  24948736 11.9G 82 Linux swap / Solaris

Partition 5 does not start on physical sector boundary.
```

I wanted to reinstall Grub, but I can't mount the partition.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

```
ubuntu@ubuntu:~$ dmesg | tail
[ 2998.613861] EXT4-fs (sda4): unable to read superblock
[ 3062.925926] EXT4-fs (sda4): unable to read superblock
[ 3062.926094] EXT4-fs (sda4): unable to read superblock
[ 3062.926269] EXT4-fs (sda4): unable to read superblock
[ 3714.162059] EXT4-fs (sda4): unable to read superblock
[ 3714.162143] EXT4-fs (sda4): unable to read superblock
[ 3714.162197] EXT4-fs (sda4): unable to read superblock
[ 4584.712409] EXT4-fs (sda4): unable to read superblock
[ 4584.712475] EXT4-fs (sda4): unable to read superblock
[ 4584.712522] EXT4-fs (sda4): unable to read superblock
```

```
ubuntu@ubuntu:~$ sudo fsck.ext4 -v /dev/sda4
e2fsck 1.42.12 (29-Aug-2014)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?
```

Testdisk 7.0 shows this:

```
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33    44 190 18     716800
 2 P HPFS - NTFS             44 190 19 22885  76 33  366933498
 3 P Windows RE(store)    22885  84 48 22946 231  5     989184
 4 E extended             22947   8 36 60801  47 46  608126978
 5 L Linux Swap           59248  51  4 60801  47 46   24948736
```


Any hints?

---

### Post by grahammechanical on 2015-08-02
It could simply be that Windows 10 has installed its own boot loader and replaced Grub with it. It could be that you used Boot Repair to install a Windows boot loader so that you could load Windows 10 and finish the upgrade. Have you tried using Boot Repair again? Let give you a report and post the URL to the report in this thread. And let us what Boot Repair sees.

At the moment it is looking like you do not have a partition for Ubuntu. sda4 is the extended partition but the only partition inside sda4 is sda5 and that is the swap partition. Where is the partition for Ubuntu?

Regards.

---

### Post by mci on 2015-08-02
Yes, I think this is the mistake that I made. I didn't choose any options, when I was running Boot Repair, so Windows installed its own boot loader. I really don't know what has happened to my partitions, since I didn't change anything "manually".

I ran Boot Repair again: [http://paste.ubuntu.com/11986990/](http://paste.ubuntu.com/11986990/)

---

### Post by oldfred on 2015-08-02
Try quick search or deeper search in testdisk.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Or try parted rescue.

You have the classic case where Windows has rewritten partition table leaving out the Linux partition in the extended partition.
Your extended partition is more like a container for logical partitions and typically you have LInux as sda5 & swap as sda6. But Windows just rewrote table with swap so it became sda5.
You show the large gap from start of extended to start of swap where your missing partition is.

      ```
 /dev/sda4       [COLOR=#ff0000]368644094[/COLOR] 976771071 608126978  290G  5 Extended
/dev/sda5       [COLOR=#ff0000]951822336[/COLOR] 976771071  24948736 11.9G 82 Linux swap / Solaris


```

You probably had a Linux partition starting one or two sectors after the start of the extended  at 3686.... and ending a few sectors before the start of swap at 9518....

       Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

---

### Post by mci on 2015-08-02
I did a deeper search with Testdisk. This is the result:

```
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              0  32 33    44 190 18     716800
 D HPFS - NTFS             44 190 19 22885  84 47  366934016
 D HPFS - NTFS          12707   8 38 23137  60 27  167561216
 D HPFS - NTFS          22885  84 48 22946 231  5     989184
 D Linux                22947   8 38 59248  51  3  583178240
 D HPFS - NTFS          23129 182 30 23142 118 16     204800
 D HPFS - NTFS          23136 250 27 33567  47 16  167561216
 D HPFS - NTFS          23142  53 16 23154 244  2     204800
 D HPFS - NTFS          28293  31 27 38723  83 16  167561216
 D HPFS - NTFS          29338 186 33 39768 238 22  167561216
 D Linux                51597 222 18 51667 251 40    1126400
 D Linux                51602 247 38 51698 148 34    1536000
 D Linux                51612  38 11 51682  67 33    1126400
 D Linux                51616  58 27 51711 214 23    1536000
 D Linux                51675  97  7 51745 126 29    1126400
 D Linux                51680 122 27 51776  23 23    1536000
 D Linux                51717  49 45 51812 205 41    1536000
 D Linux                51813  15 43 51883  45  2    1126400
 D FAT32 LBA            51818  40 63 51843 167 36     409600 [SDCARD]
 D Linux                51828  91 40 51898 120 62    1126400
 D Linux                51839 147 21 51909 176 43    1126400
 D Linux                53098  20 43 53168  50  2    1126400
 D Linux                53107  66 16 53202 222 12    1536000
 D Linux                53122 142 13 53192 171 35    1126400
 D Linux                53125 157 25 53195 186 47    1126400
 D Linux                53578 110 37 53648 139 59    1126400
 D Linux                53582 130 53 53652 160 12    1126400
 D Linux                53764  12  9 53834  41 31    1126400
 D Linux                53768  32 25 53838  61 47    1126400
 D Linux                53851 192 38 53921 221 60    1126400
 D Linux                53855 212 54 53951 113 50    1536000
 D Linux                53895 155 21 53991  56 17    1536000
 D Linux                53922  31 62 53992  61 21    1126400
 D Linux                53932  82 39 54027 238 35    1536000
 D Linux                53943 138 20 54013 167 42    1126400
 D Linux                53986  95 62 54056 125 21    1126400
 D Linux                53989 111 11 54085  12  7    1536000
 D Linux                54007 202 20 54103 103 16    1536000
 D Linux                54127  29 47 54197  59  6    1126400
 D Linux                54131  49 63 54201  79 22    1126400
 D Linux                54186  68 27 54256  97 49    1126400
 D Linux                54190  88 43 54260 118  2    1126400
 D Linux                54309 171  7 54379 200 29    1126400
 D Linux                54319 221 47 54389 251  6    1126400
 D Linux                54380  10 31 54450  39 53    1126400
 D Linux                54431   8 42 54526 164 38    1536000
 D Linux                54435  28 58 54505  58 17    1126400
 D Linux                54447  89 43 54542 245 39    1536000
 D Linux                54451 109 59 54521 139 18    1126400
 D Linux                54482   6 53 54577 162 49    1536000
 D Linux                54486  27  6 54556  56 28    1126400
 D Linux                54547  75 57 54642 231 53    1536000
 D Linux                54594  53 52 54689 209 48    1536000
 D Linux                54665 153 17 54735 182 39    1126400
 D Linux                54669 173 33 54739 202 55    1126400
 D Linux                54682 239 22 54753  13 44    1126400
 D Linux                54687   4 38 54757  33 60    1126400
 D Linux                54716 151 28 54786 180 50    1126400
 D Linux                54720 171 44 54790 201  3    1126400
 D Linux                54777 200 16 54873 101 12    1536000
 D Linux                54871 156  6 54941 185 28    1126400
 D Linux                54875 176 22 55006  59 29    2097152
 D Linux                54888 242 11 54959  16 33    1126400
 D Linux                54893   7 27 55023 145 34    2097152
 D Linux                54999  24  2 55069  53 24    1126400
 D Linux                55121 121 41 55191 150 63    1126400
 D Linux                55125 141 57 55221  42 53    1536000
 D Linux                55145 243 11 55216  17 33    1126400
 D Linux                55156  38 51 55251 194 47    1536000
 D Linux                55186 190 45 55256 220  4    1126400
 D Linux                55190 210 61 55286 111 57    1536000
 D Linux                55208  42  3 55303 197 62    1536000
 D Linux                55266  75 42 56013 217 12   12009472
 D Linux                55298 205 12 56046  91 45   12009472
 D Linux                55304   8  1 55374  37 23    1126400
 D FAT32 LBA            55308  28 17 55333 154 53     409600 [SDCARD]
 D Linux                55336 170  3 55406 199 25    1126400
 D Linux                55345 215 39 55415 244 61    1126400
 D Linux                55370  82  9 55440 111 31    1126400
 D Linux                55374 102 25 55504 240 32    2097152
 D Linux                55397 218 54 55528 101 61    2097152
 D Linux                55432 136  1 55563  19  8    2097152
 D Linux                55559 128 58 56307  15 28   12009472
 D Linux                55592   3 28 56339 144 61   12009472
 D Linux                55624 132 61 56372  19 31   12009472
 D Linux                55657   7 31 56404 149  1   12009472
 D Linux                55676 103 42 55707  98  5     497664
 D Linux                55678  48 49 55709  43 12     497664
 D Linux                55689 137  1 56437  23 34   12009472
 D Linux                55694  97 18 55725  91 44     497664
 D Linux                55695  69 53 55726  64 16     497664
 D Linux                55696  42 25 55727  36 51     497664
 D Linux                55697 242 32 55728 236 58     497664
 D Linux                55699 187 39 55730 182  2     497664
 D Linux LVM            55700  62 43 56713  55 46   16273408
 D Linux                55700  95 12 56447 236 45   12009472
 D Linux Swap           55700 127 44 55961  18 57    4186112
 D Linux                55700 160 13 55731 154 39     497664
 D Linux                55717 116 16 56465   2 49   12009472
 D Linux                55794 213 36 56542 100  6   12009472
 D Linux                55866 123  2 56614   9 35   12009472
 D Linux                55951 163 21 56021 192 43    1126400 [data]
 D Linux                55955 183 37 56051  84 33    1536000 [system]
 D Linux                56173 247 11 56244  21 33    1126400 [data]
 D Linux                56227   0 30 56322 156 26    1536000 [system]
 D Linux                56343  67 45 56413  97  4    1126400 [data]
 D Linux                56347  87 61 56442 243 57    1536000 [system]
 D Linux                56366 184 11 56462  85  7    1536000 [system]
 D Linux                56509 128  4 56517 233 36     135168
 D Linux                56516 163 32 56586 192 54    1126400 [data]
 D Linux                56520 183 48 56651  66 55    2097152 [system]
 D Linux                56533 249 37 56604  23 59    1126400 [data]
 D Linux                56538  14 53 56668 152 60    2097152 [system]
 D Linux                56566 156 39 56636 185 61    1126400 [data]
 D Linux                56569 171 51 56700  54 58    2097152 [system]
 D Linux                56609 114 18 56739 252 25    2097152 [system]
 D Linux                56730 206 53 56800 236 12    1126400
 D Linux                56767 134  8 56837 163 30    1126400 [data]
 D Linux                56771 154 24 56934 199 33    2621440 [system]
 D Linux                56773 164 32 56843 193 54    1126400 [data]
 D Linux                56777 184 48 56873  85 44    1536000 [system]
 D Linux                56789 245 33 56860  19 55    1126400 [data]
 D Linux                56794  10 49 56889 166 45    1536000 [system]
 D Linux                56822 152 35 56892 181 57    1126400 [data]
 D Linux                56825 167 47 56921  68 43    1536000 [system]
 D Linux                56862  95  2 56957 250 61    1536000 [system]
 D Linux                56970 121 48 57040 151  7    1126400 [data]
 D Linux                56974 142  1 57137 187 10    2621440 [system]
 D Linux                57003  28 50 57073  58  9    1126400 [data]
 D Linux                57006  43 62 57169  89  8    2621440 [system]
 D Linux                57026 145 16 57189 190 25    2621440 [system]
 D Linux                57042 226 17 57206  16 26    2621440 [system]
 D Linux                57241 193 41 57311 222 63    1126400 [data]
 D Linux                57245 213 57 57341 114 53    1536000 [system]
 D Linux                57263  44 62 57333  74 21    1126400 [data]
 D Linux                57267  65 15 57362 221 11    1536000 [system]
 D Linux                57298 222 13 57368 251 35    1126400 [data]
 D Linux                57302 242 29 57398 143 25    1536000 [system]
 D Linux                57323  88 46 57418 244 42    1536000 [system]
 D Linux                57422  69 56 57492  99 15    1126400
 D Linux                57476  83 16 57546 112 38    1126400 [data]
 D Linux                57480 103 32 57610 241 39    2097152 [system]
 D Linux                57492 164 17 57562 193 39    1126400 [data]
 D Linux                57496 184 33 57627  67 40    2097152 [system]
 D Linux                57525  71 19 57595 100 41    1126400 [data]
 D Linux                57529  91 35 57659 229 42    2097152 [system]
 D Linux                57549 192 52 57680  75 59    2097152 [system]
 D Linux                57551 202 60 57682  86  4    2097152 [system]
 P Linux Swap           59248  51  4 60801  47 46   24948736



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, blocksize=4096, 367 MB / 350 MiB
```

After ENTER:
```

TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33    44 190 18     716800
 2 P Linux Swap           59248  51  4 60801  47 46   24948736


>[  Quit  ]  [ Write  ]
```

I dont know what to do next.

---

### Post by mci on 2015-08-02
I get this when performing a Quick Search:

```
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
>D HPFS - NTFS              0  32 33    44 190 18     716800
 D HPFS - NTFS             44 190 19 22885  84 47  366934016
 D HPFS - NTFS          22885  84 48 22946 231  5     989184
 D Linux                22947   8 38 59248  51  3  583178240
 D Linux Swap           59248  51  4 60801  47 46   24948736
```

I can also list the files from the Linux partition:
```

TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
     Linux                22947   8 38 59248  51  3  583178240
Directory /

>drwxr-xr-x     0     0      4096 28-Jul-2015 07:59 .
 drwxr-xr-x     0     0      4096 28-Jul-2015 07:59 ..
 drwx------     0     0     16384 23-Feb-2015 14:40 lost+found
 drwxr-xr-x     0     0     12288  1-Aug-2015 16:31 etc
 drwxr-xr-x     0     0      4096 23-Feb-2015 14:47 media
 drwxr-xr-x     0     0      4096 18-Feb-2015 19:41 var
 drwxr-xr-x     0     0      4096 31-Jul-2015 09:37 bin
 drwxr-xr-x     0     0      4096 29-Jul-2015 19:06 boot
 drwxr-xr-x     0     0      4096 18-Feb-2015 19:37 dev
 drwxr-xr-x     0     0      4096 23-Feb-2015 14:42 home
 drwxr-xr-x     0     0      4096 26-May-2015 20:02 lib
 drwxr-xr-x     0     0      4096 27-Feb-2015 12:37 lib64
 drwxr-xr-x     0     0      4096 15-Apr-2015 08:15 mnt
 drwxr-xr-x     0     0      4096 23-Jul-2015 07:55 opt
 drwxr-xr-x     0     0      4096 10-Apr-2014 22:12 proc
 drwx------     0     0      4096 17-Jul-2015 09:42 root
 drwxr-xr-x     0     0      4096 18-Feb-2015 19:38 run
 drwxr-xr-x     0     0     12288 31-Jul-2015 09:37 sbin
 drwxr-xr-x     0     0      4096 18-Feb-2015 19:32 srv
 drwxr-xr-x     0     0      4096 13-Mar-2014 01:41 sys
 drwxrwxrwt     0     0      4096  1-Aug-2015 16:31 tmp
 drwxr-xr-x     0     0      4096  4-Jun-2015 16:00 usr
 lrwxrwxrwx     0     0        30 28-Jul-2015 07:59 vmlinuz
 lrwxrwxrwx     0     0        33 28-Jul-2015 07:59 initrd.img
 drwxr-xr-x     0     0      4096 23-Feb-2015 14:41 cdrom
 -rw-r--r--     0     0         0 14-May-2015 07:44 0
 lrwxrwxrwx     0     0        33 23-Jul-2015 07:56 initrd.img.old
 lrwxrwxrwx     0     0        30 23-Jul-2015 07:56 vmlinuz.old
 drwxr-xr-x     0     0      4096 14-Apr-2015 07:51 lib32
 lrwxrwxrwx     0     0        30 23-Jul-2015 07:56 vmlinuz.10001

                                                   Next
Use Right to change directory, h to hide deleted files
    q to quit, : to select the current file, a to select all files
    C to copy the selected files, c to copy the current file
```

But unfortunatly I don't know where to go from here. I'm afraid I will mess something up.

EDIT: I also tried parted rescue, but it didn't find any deleted partitions.

---

### Post by oldfred on 2015-08-02
You want to add this to the one's you show in your first post. And it needs to be logical or L.

```

D Linux                22947   8 38 59248  51  3  583178240
```

Your deeper search is  showing your Ubuntu install in above partition.

You must have repartitioned several times, as it is showing many partitions, but you want to keep all the existing & add just the one with your install.
Do not write without all partitions you currently have.

---

### Post by mci on 2015-08-02
I did a mistake while using parted. Now I do get a result. It looks very promising.

```
lubuntu@lubuntu:~$ sudo parted
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) rescue                                                           
Start? 368642047                                                          
End? 976771071                                                            
Information: A ext4 logical partition was found at 368644096s -> 951822335s.  Do you want to add it to the partition
table?
Yes/No/Cancel? yes
(parted) p                                                                
Model: ATA ST500LM000-SSHD- (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      2048s       718847s     716800s     primary   ntfs            boot
 2      718848s     367652345s  366933498s  primary   ntfs
 3      367652864s  368642047s  989184s     primary   ntfs            diag
 4      368644094s  976771071s  608126978s  extended
 6      368644096s  951822335s  583178240s  logical   ext4
 5      951822336s  976771071s  24948736s   logical   linux-swap(v1)

(parted)
```

Oldfred, I am sorry for the mix up. Should I write this partion table? What about the number 4 and number 6, are they not colluding?

EDIT: I also did a backup of the partion table like you suggested in another thread with: [FONT=courier new] sudo sfdisk -d /dev/sda > PT.txt[/FONT]

---

### Post by oldfred on 2015-08-02
Good to have backup, just in case.

Yes write that version, as it looks correct.
The extended partition is like a container for all logical partitions. Or all logical partitions must be inside the extended.

The only minor issue may be that your original install probably had the Linux as sda5 & swap as sda6. But since Ubuntu changed to using UUID many years ago & partition restore should keep same UUID, it may just boot from grub.  I would run a sudo update-grub if it does boot. 
There may be some places where an older device setting like /dev/sda5 is used, so if any other issues check that first.

---

### Post by mci on 2015-08-02
I am back on my machine again. Thank you very much for your help!!! :)

---

