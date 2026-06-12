---
title: "Making partitions and mount points more efficient/logical?"
date: 2017-07-20
forum: General Help
---

### Post by hooker2 on 2017-07-20
I have a Linux box (Ubuntu 16.04 LTS) which is primarily used as a media server and the brains for a wired home. Ubuntu was installed on a smallish HD and has run out of space so I'm constantly getting errors and am unable to run programs without restarting (to presumably clear the cache). I'm hoping to get some suggestions on how to properly set up my partitions and mount points in order to get it running more efficiently.

Abbreviated fdisk -l:
```

Disk /dev/sda: 152.7 GiB, 163928604672 bytes, 320173056 sectors
Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 320172031 319170562 152.2G  5 Extended
/dev/sda5       1001472 320172031 319170560 152.2G 8e Linux LVM

Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Device         Start        End   Sectors   Size Type
/dev/sdb1       2048  976762879 976760832 465.8G Linux LVM
/dev/sdb2  976762880 1953523711 976760832 465.8G Linux LVM

Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 5860532223 5860530176  2.7T Linux filesystem

Disk /dev/sdd: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Device     Start        End    Sectors  Size Type
/dev/sdd1   2048 5860532223 5860530176  2.7T Linux filesystem

Disk /dev/md0: 2.7 TiB, 3000457232384 bytes, 5860268032 sectors
Disk /dev/mapper/ubuntu--vg-root: 610.3 GiB, 655259336704 bytes, 1279803392 sectors
Disk /dev/mapper/ubuntu--vg-swap_1: 7.7 GiB, 8254390272 bytes, 16121856 sectors
Disk /dev/mapper/cryptswap1: 7.7 GiB, 8253865984 bytes, 16120832 sectors
Disk /dev/mapper/home--vg-home: 465.8 GiB, 500099448832 bytes, 976756736 sectors
```

I just added a 1 TB drive (sdb) with the intent to open up some breathing room on the boot/install disk (sda). The two 3 TB drives (sdc & sdd) are mirrored in md0 and should only serve as data drives.

My thought was to make sda boot only and move all of the "other stuff" over to sdb. I'm thinking I need to shrink my root volume to a single drive (sdb1; it is currently spanning sda5 and sdb1) and move home and whatever else is extraneous to sdb2, leaving the entire sda for boot and swap.

Does this even make sense?

---

### Post by gsahli on 2017-07-20
I'm not sure if this fits your situation, but...
3 home desktops use this arrangement - SSD is boot drive and has all system files (incl applications), and my home folder. I've created Documents, Downloads, Music, Pictures, Videos folders on a second drive and used soft links within my home folder to all those (standard) data folders on the second drive.
I think it is important to keep my home folder on the SSD because the hidden profile/preference files there need to have fast access.

---

### Post by vocx on 2017-07-20
> **hooker2 said:**
> I have a Linux box (Ubuntu 16.04 LTS) which is primarily used as a media server and the brains for a wired home. Ubuntu was installed on a smallish HD and has run out of space so I'm constantly getting errors and am unable to run programs without restarting (to presumably clear the cache). I'm hoping to get some suggestions on how to properly set up my partitions and mount points in order to get it running more efficiently.

Abbreviated fdisk -l:
```

Disk /dev/sda: 152.7 GiB, 163928604672 bytes, 320173056 sectors
Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 320172031 319170562 152.2G  5 Extended
/dev/sda5       1001472 320172031 319170560 152.2G 8e Linux LVM

Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Device         Start        End   Sectors   Size Type
/dev/sdb1       2048  976762879 976760832 465.8G Linux LVM
/dev/sdb2  976762880 1953523711 976760832 465.8G Linux LVM

...
```

I just added a 1 TB drive (sdb) with the intent to open up some breathing room on the boot/install disk (sda). The two 3 TB drives (sdc & sdd) are mirrored in md0 and should only serve as data drives.

My thought was to make sda boot only and move all of the "other stuff" over to sdb. **I'm thinking I need to shrink my root volume to a single drive (sdb1; it is currently spanning sda5 and sdb1)** and move home and whatever else is extraneous to sdb2, leaving the entire sda for boot and swap.

Does this even make sense?
I don't understand this shrinking of root volume, but it's probably because you are using LVM and I haven't used that.

I see one drive of 152 GB (sda), and another of 1 TB (sdb). I would make the first drive only for the operating system, that is "/" and swap, and the second disk for your personal files, or "/home".
```

# device      mount point     size
/dev/sda1    /              136 GB
/dev/sda2    swap            16 GB

/dev/sdb1    /home            1 TB

```

So, yes, what you are saying makes sense. One drive for the system, one for your files.

Although, I am wondering, what do you have in your system that you are running out of space? If you are downloading things all the time, you should download them to your "/home" directory, which should not run out of space at 1 TB of space. The system files reside mostly in "/usr" and "/var". Most installed programs reside in "/usr". All the packages you download with APT, and logs, usually reside somewhere in "/var", so that may be taking space. You should clean up things. There may also be some hidden files under your user home directory, in "/home/user/.cache", for example.
```

# check your space with
df -h
ncdu

```

You also have a small "sda1" partition of 487 MB. What is this for? Maybe "/boot"? If you get errors that you are running out of space maybe is because you have many old kernels here that you don't need any more, and thus you should remove them using "apt remove". Moreover, keeping a "/boot" partition that small is not good. Given that you have plenty of space, you should make sure "/boot" is in the same partition as "/" so it uses the entire 136 GB of space for storing kernels, and not only 487 MB. As a matter of fact, the operating system itself, with many many packages installed (video players, games, office suite, email), should probably not be larger than 30 GB. So it is puzzling to me that your system is running out of space.
```

# clean
sudo apt clean
sudo apt autoremove
sudo apt remove linux-image-[version]-generic

```

---

### Post by hooker2 on 2017-07-21
[QUOTE=vocx]
```

# device      mount point     size
/dev/sda1    /              136 GB
/dev/sda2    swap            16 GB

/dev/sdb1    /home            1 TB

```[/QUOTE]

This is a much better explanation of what I am proposing. I'm glad to see I was on the right track.

[QUOTE=vocx]Although, I am wondering, what do you have in your system that you are running out of space? ... You also have a small "sda1" partition of 487 MB. What is this for? Maybe "/boot"?[/QUOTE]

Forgot to include the boot error, my apologies. You nailed it, though. For some silly reason /boot is on an abysmally small partition so it has zero bytes left making it a PITA to do anything without restarting the computer.

I'll try the recommendations and see how it works out. Thanks guys!

---

### Post by Cavsfan on 2017-07-21
You can also label your partitions which makes them display as the name instead of say **/dev/sda2**

If it is a one word name, this will work:
 ```
sudo tune2fs -L Xenial /dev/sda2
```

If it's more than one word just wrap quotes around it:
```
sudo tune2fs -L "Xenial Xerus" /dev/sda2
```

```
cavsfan@cavsfan-Le-Beast:~$ sudo blkid
/dev/sda6: LABEL="Zesty" UUID="c1549566-ed28-48f2-a546-b8a5b39729d6" TYPE="ext4" PARTUUID="a55f55ec-06"
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" PARTUUID="a55f55ec-01"
/dev/sda2: LABEL="Arch-Install" UUID="97ce09d6-b701-499e-b838-93762e3b005c" TYPE="ext4" PARTUUID="a55f55ec-02"
/dev/sda4: LABEL="Xenial" UUID="09320a63-c5e5-4e47-afab-dfa5f9a5d8dc" TYPE="ext4" PTTYPE="dos" PARTUUID="a55f55ec-04"
/dev/sda5: UUID="3e98ebb1-3a5e-46d2-9302-6e4a811e644b" TYPE="swap" PARTUUID="a55f55ec-05"
/dev/sda7: LABEL="Artful" UUID="6e2a8ddf-f892-4ce9-82c4-21e45f28df3b" TYPE="ext4" PARTUUID="a55f55ec-07"
/dev/sdb1: LABEL="Fantom" UUID="B266B4B166B47825" TYPE="ntfs" PARTUUID="f87b4c9a-01"

```
I have an older computer but, all of my partitions are labeled for simplification.

---

### Post by hooker2 on 2017-07-21
> **Cavsfan said:**
> /dev/sda6: LABEL="Zesty" UUID="c1549566-ed28-48f2-a546-b8a5b39729d6" TYPE="ext4" PARTUUID="a55f55ec-06"

Zesty! Ha.

That's a good idea, thanks.

---

### Post by Cavsfan on 2017-07-22
> **Cavsfan said:**
> /dev/sda6: LABEL="Zesty" UUID="c1549566-ed28-48f2-a546-b8a5b39729d6" TYPE="ext4" PARTUUID="a55f55ec-06"

> **hooker2 said:**
> Zesty! Ha.

That's a good idea, thanks.

You are welcome! Why make it hard when it can be easy.

This is much more easy to understand than looking at /dev/sda5/, blah, blah, blah...

[ATTACH=CONFIG]276104[/ATTACH]

---

