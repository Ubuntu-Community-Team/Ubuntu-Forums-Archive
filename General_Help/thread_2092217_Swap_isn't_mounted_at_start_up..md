---
title: "Swap isn't mounted at start up."
date: 2012-12-07
forum: General Help
---

### Post by lved on 2012-12-07
Hi there.

My swap partition isn't mounted at start up and I don't have any idea what's the problem.
Maybe someone of you can help me.

Thank you.

> eg@eg-ae:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=634b4eea-e5dd-4e1d-948b-9536a60d31d5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=44cc4e91-4017-438b-a2ae-cb302dcf1957 none            swap    sw              0       0

UUID=921E99DD1E99BAA5 none ntfs ro,noauto 0 0
UUID=70CCBD45CCBD067E none ntfs ro,noauto 0 0
#/dev/sda none ntfs,ro 0 0
eg@eg-ae:~$ ll /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 140 Dec  7  2012 ./
drwxr-xr-x 6 root root 120 Dec  7  2012 ../
lrwxrwxrwx 1 root root  10 Dec  7 09:22 44cc4e91-4017-438b-a2ae-cb302dcf1957 -> ../../sda7
lrwxrwxrwx 1 root root  10 Dec  7 09:22 634b4eea-e5dd-4e1d-948b-9536a60d31d5 -> ../../sda6
lrwxrwxrwx 1 root root  10 Dec  7 09:22 65CDBE7F6511CD2D -> ../../sda5
lrwxrwxrwx 1 root root  10 Dec  7 09:22 70CCBD45CCBD067E -> ../../sda1
lrwxrwxrwx 1 root root  10 Dec  7 09:22 921E99DD1E99BAA5 -> ../../sda2
eg@eg-ae:~$ sudo fdisk /dev/sda
[sudo] password for eg: 

Command (m for help): p

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10a234e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   200206847   100000000    7  HPFS/NTFS/exFAT
/dev/sda3       200208382   976771071   388281345    5  Extended
/dev/sda5       400209920   960765951   280278016   83  Linux
/dev/sda6       200208384   400207871    99999744   83  Linux
/dev/sda7       960768000   976771071     8001536   82  Linux swap / Solaris

Partition table entries are not in disk order

Command (m for help): q

eg@eg-ae:~$ swapon -s
Filename                Type        Size    Used    Priority
eg@eg-ae:~$ sudo swapon -a
eg@eg-ae:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda7                               partition    8001532    0    -1


---

### Post by CaptainMark on 2012-12-07
This is strange, are you sure your swap partition matches the UUID your /etc/fstab file has listed for it, find the UUID with ```
sudo blkid
```and /dev/sda7 should read 44cc4e91-4017-438b-a2ae-cb302dcf1957 if not then change your fstab file to match blkid, if they do match try removing the uuid from fstab and using /dev/sda7 instead

---

### Post by HermanAB on 2012-12-07
BTW, read the swapon man page.  Everything you would ever want to know about swap is in there.

---

### Post by rnerwein on 2012-12-07
> **HermanAB said:**
> BTW, read the swapon man page.  Everything you would ever want to know about swap is in there.
lved has a problem that as shown can be fixed manualy.
i have a problem (wrote a thread about 2 month ago - no answer). will place my problem here ( may be now any body have an idea)

----------------------[COLOR=Blue] what's going on with /dev/sda5 == first  swap device [/COLOR]----------------
1. [COLOR=Red]swapon -s[/COLOR]
   /dev/sdb5                               partition    4466032 0   -1

2. [COLOR=Red]swapon -a[/COLOR] 
   swapon: cannot find the device for UUID=9479038f-f5d7-4a4b-8ff3-5afd28bb3e16

3. cat /proc/swaps
/dev/sdb5                               partition   4466032 0   -1

4.[COLOR=Red] grep swap /etc/fstab[/COLOR]
UUID=9479038f-f5d7-4a4b-8ff3-5afd28bb3e16 none  swap    sw    0       0 (sda5)
UUID=4214ad22-10b7-4420-8560-236b7d800467 none  swap    sw    0       0 (sdb5)
5.[COLOR=Red] blkid[/COLOR]
/dev/sda5: UUID="9479039f-f5d7-4a4b-8ff3-5afd28bb3e16" TYPE="swap"
/dev/sdb5: UUID="4214ad22-10b7-4420-8560-236b7d800467" TYPE="swap"

6.[COLOR=Red] fdisk -l[/COLOR]
/dev/sda5       940862853   945071819     2104483+  82  Linux Swap / Solaris
/dev/sdb5        84003948    92936024     4466038+  82  Linux Swap / Solaris

7.[COLOR=Red] swapon: -f -v[/COLOR] 9479039f-f5d7-4a4b-8ff3-5afd28bb3e16: &#8222;stat&#8220; gescheitert.: Datei oder 
                    Verzeichnis nicht gefunden (file or directory not found)

8.[COLOR=Red] ls -l /dev/sda5[/COLOR]
           brw-rw---- 1 root disk 8, 5 Dez  7 11:29 /dev/sda5
     
9.[COLOR=Red] grep sda5 [COLOR=Black]/var/log/kern.log[/COLOR][/COLOR]
Dec  7 07:31:17 tschang kernel: [    1.315760]  sda: sda1 sda2 sda3 sda4 < [COLOR=Red]sda5[/COLOR] sda6 sda7 sda8 >

10. my brain fried - core dumped

any idea - help

---

### Post by HermanAB on 2012-12-07
2. swapon -a
swapon: cannot find the device for UUID=9479038f-f5d7-4a4b-8ff3-5afd28bb3e16

Well, there is your error.

Either fix the UUID or don't use UUIDs, but rather the device names such as /dev/sdb or whatever.

---

### Post by lved on 2012-12-07
[LEFT] > 4.[COLOR=Red] grep swap /etc/fstab[/COLOR]
UUID=947903**8**f-f5d7-4a4b-8ff3-5afd28bb3e16 none  swap    sw    0       0 (sda5)
UUID=4214ad22-10b7-4420-8560-236b7d800467 none  swap    sw    0       0 (sdb5)
5.[COLOR=Red] blkid[/COLOR]
/dev/sda5: UUID="947903**9**f-f5d7-4a4b-8ff3-5afd28bb3e16" TYPE="swap"
/dev/sdb5: UUID="4214ad22-10b7-4420-8560-236b7d800467" TYPE="swap"The UUID from the fstab is different to the UUID from blkid.


Back to my case:
Are blkid and  ll /dev/disk/by-uuid/ using different resources?
Whatever - UUID is correct.

tried it with /dev/sda7 in the fstab - no change at all.
swapon -a stillworking.


> eg@eg-ae:~$ sudo blkid
[sudo] password for eg: 
/dev/sda1: LABEL="SYSTEM" UUID="70CCBD45CCBD067E" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="921E99DD1E99BAA5" TYPE="ntfs" 
/dev/sda5: LABEL="STORAGE" UUID="65CDBE7F6511CD2D" TYPE="ntfs" 
/dev/sda6: UUID="634b4eea-e5dd-4e1d-948b-9536a60d31d5" TYPE="ext4" 
/dev/sda7: UUID="44cc4e91-4017-438b-a2ae-cb302dcf1957" TYPE="swap" 
eg@eg-ae:~$ sudo vim /etc/fstab
eg@eg-ae:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=634b4eea-e5dd-4e1d-948b-9536a60d31d5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
#UUID=44cc4e91-4017-438b-a2ae-cb302dcf1957 none            swap    sw              0       0
/dev/sda7 none            swap    sw              0       0
UUID=921E99DD1E99BAA5 none ntfs ro,noauto 0 0
UUID=70CCBD45CCBD067E none ntfs ro,noauto 0 0
#/dev/sda none ntfs,ro 0 0
[/LEFT]

---

### Post by rnerwein on 2012-12-07
> **HermanAB said:**
> 2. swapon -a
swapon: cannot find the device for UUID=9479038f-f5d7-4a4b-8ff3-5afd28bb3e16

Well, there is your error.

Either fix the UUID or don't use UUIDs, but rather the device names such as /dev/sdb or whatever.

1. UUID=9479038f-f5d7-4a4b-8ff3-5afd28bb3e16
 2. swapon: cannot find the device for 
    UUID=9479038f-f5d7-4a4b-8ff3-5afd28bb3e16

 sorry where is my error ?

 1. and 2. are always identical. in fstab, swapon -a, blkid and fisk -l.
 even /dev/sda5 is always the same (/dev/sdb5 is the second disk there is no problem with the swap device  i have  the problem with the swap on /dev/sda5)
 and now ???? :-(

---

### Post by oldfred on 2012-12-07
I have never seen none used for anything other than swap.
in fstab that none would specify that the partition has none fs type.

> UUID=921E99DD1E99BAA5 [COLOR=Red]none[/COLOR] ntfs ro,noauto 0 0
UUID=70CCBD45CCBD067E[COLOR=Red] none [/COLOR]ntfs ro,noauto 0 0
Generally you still need to create a mount point even if you do not want to mount it with noauto.

Some examples I copied from somewhere, but you have to create the mounts:

       Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

Edit - I did find that Macs use none as a entry, but have not found it in fstab. It may also be used with bind, but I do not know bind.

---

### Post by lved on 2012-12-08
> **rnerwein said:**
> 1. UUID=9479038f-f5d7-4a4b-8ff3-5afd28bb3e16
 2. swapon: cannot find the device for 
    UUID=9479038f-f5d7-4a4b-8ff3-5afd28bb3e16

 sorry where is my error ?

 1. and 2. are always identical. in fstab, swapon -a, blkid and fisk -l.
 even /dev/sda5 is always the same (/dev/sdb5 is the second disk there is no problem with the swap device  i have  the problem with the swap on /dev/sda5)
 and now ???? :-(

@[COLOR=Orange]**[rnerwein]("http://ubuntuforums.org/member.php?u=972890")**[/COLOR] Have you read my post too?
Your UUID is wrong, check it with sudo blkid - I marked the difference between this two UUIDs out earlier.

@[[COLOR=#DD4814]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711") It's not a problem with the ntfs. I don't want them to be mounted by Ubuntu by default.

---

### Post by rnerwein on 2012-12-08
> **lved said:**
> [LEFT] The UUID from the fstab is different to the UUID from blkid.


Back to my case:
Are blkid and  ll /dev/disk/by-uuid/ using different resources?
Whatever - UUID is correct.

tried it with /dev/sda7 in the fstab - no change at all.
swapon -a stillworking.


[/LEFT]

oh my god
lved got eyes like a lynx ( that's what we say in german - means althogh eyes like an eagle)
takes me hours and i can't find the differents of the blkid's
fstab ->  UUID="947903[COLOR=Red]8[/COLOR]f-f5d7-4a4b-8ff3-5afd28bb3e16" TYPE="swap"
blkid ->  UUID="947903[COLOR=Blue]9[/COLOR]f-f5d7-4a4b-8ff3-5afd28bb3e16" TYPE="swap" 
                                                                                        **[COLOR=Red]  -------------------------------- |[/COLOR]**

where does this come from - dosen't matter the problem is fixed 
thank's much lved

---

### Post by lved on 2012-12-10
@oldfred: It seems your suggestion was right. The incorrect NTFS entries lead to the failure.
@rnerwein: I understand this saying, my native language is also German. Glad you could solve the problem. :)

Solution: I removed the faulty NTFS entries, the swap partition is now mounted at start up.

---

### Post by rnerwein on 2012-12-10
> **lved said:**
> @oldfred: It seems your suggestion was right. The incorrect NTFS entries lead to the failure.
@rnerwein: I understand this saying, my native language is also German. Glad you could solve the problem. :)

Solution: I removed the faulty NTFS entries, the swap partition is now mounted at start up.
by the side: swap is never mounted it is assigned to the system ( swap wird nicht gemounted sondern dem system zugeordnet - egal hauptsache man versteht was gemeint ist)
tschau

---

### Post by rnerwein on 2012-12-10
> **lved said:**
> @oldfred: It seems your suggestion was right. The incorrect NTFS entries lead to the failure.
@rnerwein: I understand this saying, my native language is also German. Glad you could solve the problem. :)

Solution: I removed the faulty NTFS entries, the swap partition is now mounted at start up.
by the side: swap is never mounted it is assigned to the system ( swap wird nicht gemounted sondern dem system zugeordnet - egal hauptsache man versteht was gemeint ist)
tschau

---

