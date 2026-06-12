---
title: "Grub 2Tb limitation"
date: 2021-12-21
forum: General Help
---

### Post by davidricq87 on 2021-12-21
Hi,

I just expand a virtual disk from 2Tb to 3Tb.

After update to the latest kernel, I was not able to boot "error: attempt to read or write outside of disk 'hd0'".

After a almost heart attack and check everything, I notice some /boot files fragment was after 2.2TB. So I move everything in boot to a new virtual hard drive, setup fstab and grub.

Why grub can't read file after 2TB ? Where this limitation come from ? And why there is no warning message during grub-update ?

---

### Post by oldfred on 2021-12-21
What part of grub.
Grub in ESP for UEFI boot, grub in bios_grub for BIOS boot? Or grub in / (root) and you have a very large /?
If 3TB, you have to have gpt, so one or the other partitions for grub to install correctly.
Post this:
sudo parted -l

There have been similar issues.
Years ago it was a BIOS issue where user had 20GB drives & updated to new larger drives. BIOS had limit of 37GB.
And grub had issue when 1TB drives became more common. It had a limit of 600? GB which was fixed, but I do not know know how large they made it.
I also though I saw somewhere that ESP cannot be beyond 2TiB either as then UEFI cannot find it. UEFI suggests ESP be first partition.

Most do not have / (root) that large.
First partition is ESP or bios_grub, then a / & then either /home or data partition(s). So then not an issue.

---

### Post by davidricq87 on 2021-12-22
I had everything in a single partition : 


```

Model: QEMU QEMU HARDDISK (scsi)
Disk /dev/sda: 3273GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  3273GB  3273GB  ext4

```

Grub files : 

```

sda2: Location of files loaded by Grub 
GiB - GB                        File                                 Fragment(s)
2075.709274292 = 2228.775862272 boot/grub/i386-pc/core.img          1 
701.773494720 = 753.523552256     boot/vmlinuz-4.15.0-162-generic     5
308.244201660 = 330.974691328     boot/vmlinuz-4.15.0-163-generic     2
308.244201660 = 330.974691328     vmlinuz                             2
701.773494720 = 753.523552256     vmlinuz.old                         5
663.097652435 = 711.995682816     boot/initrd.img-4.15.0-163-generic     8
663.097652435 = 711.995682816     initrd.img                             8 

```



>  Most do not have / (root) that large.
I take notes. The lesson is learned. Now, I want to know why.

---

### Post by oldfred on 2021-12-22
Do not know details on grub other than the bit of history I posted above.
You could file bug report, but with 22.04 they are changing from grub 2.04 to 2.06.

I use 30GB or so for / with my Kubuntu installs. But currently do not allow snaps which can take a lot of room. But it looks like Kubuntu 22.04 now uses the Firefox snap.
But I put all data normally in /home into a large data partition or two, including some normally hidden data files in /home, so /home is now small (~300MB).

Showing only partiitons, not tempfs.

> fred@z97-focal-kubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        24G   13G   11G  56% /
/dev/sdb4       385G  142G  224G  39% /mnt/data

---

### Post by TheFu on 2021-12-22
I don't know about grub limitations. Sorry.

I use 1GB - 35GB for the OS, never more.

For data, that goes to other locations and is sized for what is needed for the next few months.

In the old days, we'd setup separate partitions for 
[LIST]
[*]/
[*]/boot
[*]/var
[*]/usr
[*]/home and 
[*]/etc
[*]/export or /nfs
[/LIST]
because there were bad things that could happen if any of those filled up, but we didn't have 14TB drives.  /usr and some home directories were often mounted over the network using NFS. We'd have other storage available via NFS too. I still follow those rules to avoid problems. That's what being an experienced admin teaches - _avoiding issues sooner is better than fixing them later._

In more recent times, there was the MBR partition table problem with partitions over 2TB not working. In theory, GPT removed that limit, but I've honestly never tested it.
For me, partitioning is connected to how I will backup the data.  I generally don't backup the OS, just the OS settings and the list of packages manually installed. Then at recovery time, I begin with a minimal, OS install to a partition just for the OS.
I've been lazy on this desktop install:
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   19G   12G  6.2G  66% /
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
/dev/mapper/vgubuntu--mate-home ext4   12G  7.2G  4.0G  65% /home
istar:/d/D1                     nfs4  3.5T  3.5T   18G 100% /d/D1
istar:/d/D2                     nfs4  3.6T  3.5T   28G 100% /d/D2
istar:/d/D3                     nfs4  3.6T  3.6T   19G 100% /d/D3
romulus:/raid/media             nfs4  1.8T  1.7T   12G 100% /R
romulus:/Data/r2                nfs4  1.3T  1.2T   61G  95% /S
romulus:/raid/media/Music       nfs4  1.8T  1.7T   12G 100% /M

$ sudo vgs
  VG            #PV #LV #SN Attr   VSize  VFree
  vgubuntu-mate   2   3   0 wz--n- **39.49g** 4.39g

$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home   vgubuntu-mate -wi-ao---- 12.00g                                                    
  root   vgubuntu-mate -wi-ao---- 19.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g                
```
As you can see, most of the storage is on NFS.  Just 40G is available "on" the desktop itself.  BTW, this is a 20.04 install. If I were doing it again today, I'd do something like described here: [Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)
I think 25G has been proven to be a little small for people allowing snap packages and a swap file in /.  I keep swap separate and either prevent or severely limit the use of snap packages.

Most of my systems got their disk setups before 2015, so they aren't "perfect" ... but I've learned that perfect is just my best guess at the time, which is always subject to change as needs get altered. For example, a media server here (I use both plex and jellyfin) outgrew the available storage in /var, so I created new places for all that media metadata.
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--8TB--B-jellyfin_varlib   ext4   89G  6.9G   77G   9% /var/lib/jellyfin
/dev/mapper/istar--8TB--B-plex_varlib       ext4   89G   41G   44G  49% /var/lib/plexmediaserver

```
Note how I mounted the storage under /var/lib/ for each?  That's where the extra storage was needed, so I placed it exactly there. I guessed that jellyfin would need the same amount of storage that plex used.  I was wrong. Interesting.  I'm just a terrible guesser.

---

