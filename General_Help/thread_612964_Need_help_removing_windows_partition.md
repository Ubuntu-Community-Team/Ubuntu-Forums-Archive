---
title: "Need help removing windows partition"
date: 2007-11-14
forum: General Help
---

### Post by MightyMe on 2007-11-14
I'm having a dual boot system with Gutsy and XP and managed to somehow mess up my Windows XP.  The Windows boot sequence starts but crashes after a while. So, I automatically mount the NTFS partition instead in Ubuntu using the NTFS configuration tool which btw works great.

You can see my fdisk listing below and I have some questions:
1. Can I format the NTFS partition considering the boot flag? If so, how?
2. Would a formatting of the NTFS partition do non-wanted things to Grub?
3. Can I append that partition to my Linux partition?
4. If I succeed in formatting the partition, do I just uninstall the NTFS tool to avoid automatically mount it at boot?

Any help would be appreciated.

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6515    52331706    7  HPFS/NTFS
/dev/sda2            6516        9590    24699937+  83  Linux
/dev/sda3            9591        9729     1116517+   5  Extended
/dev/sda5            9591        9729     1116486   82  Linux swap / Solaris

---

### Post by MightyMe on 2007-11-14
bump

---

### Post by kaiju on 2007-11-14
1. Can I format the NTFS partition considering the boot flag? If so, how?

if you want to format the partition, i recommend gparted, as it gives you visual feedback of what you are doing (the version currently available for gutsy has a bug causing it to crash when refreshing the device table, but that shouldn't scare you off because it happens after all work is already done). i suppose you can also keep the boot flag if you want to or set it to any other partition on the disk - right click on the partition and 'manage flags' in gparted (on my hd for ex., the swap partition has the boot flag).

2. Would a formatting of the NTFS partition do non-wanted things to Grub?

if you format the partition or merge it with another one and don't want to boot anything from it, you should comment out its entry in /boot/grub/menu.lst, through
```
sudo gedit boot/grub/menu.lst
```
and putting a # in front of every line for your former winxp installation (it should be near the bottom of the file)

3. Can I append that partition to my Linux partition?

if you want to append it to another partition, you can delete it and increase the size of the other partition to incorporate the empty space. if they are not next to each other, you move partitions around until they are.
if you want to append the empty space to your current root partition, you need to boot from the livecd and use gparted from there.

4. If I succeed in formatting the partition, do I just uninstall the NTFS tool to avoid automatically mount it at boot?

i don't know anything about ntfs tool, but everything that gets mounted at bootup should be contained in your /etc/fstab file.
if you don't move the partition or change its size, only format it to ext3, you only have to rewrite the <type> part and some <options>:
```
sudo gedit /etc/fstab
```
and then for ex:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda6          /mnt/sda6           ntfs    defaults,utf8,umask=007,gid=46 0       1

```
becomes
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda6          /mnt/sda6           ext3    defaults    0    2

```

if you move partitions or change their sizes and your entries look like this:
```

# /dev/sda2
UUID=59c4f021-5dc1-48d7-8ffc-552f7935bf91 /mnt/sda2       ext3    defaults        0       2

```
with device id's specified, then you need to remove the uuid=blahblah parts so that your entries will look like this
```

/dev/sda2    /mnt/sda2       ext3    defaults        0       2

```
(you might want to look up what uuid is good for, before doing this, but from my humble experience i'd say it changes nothing, and i keep them disabled because i move around partitions a lot)

if you are merging the partition into another one, you should completely remove the former's entry.

oh, and before editing anything important, it's always wise to make a backup copy, like:
```
sudo cp /etc/fstab /etc/fstab.bak
```

peace.


p.s.
what is a "bump"?

---

### Post by MightyMe on 2007-11-15
Many thanks for the help kaiju. I will give it a try soon.

 Btw, I had to google "bump" myselft :) 
Apparently  i means "Bring Up My Post" and it's used in forums everywhere in order to make the thread more active in the listings. It's sort of a  bogus reply to make it show.

---

### Post by kaiju on 2007-11-15
about those uuid's, because you probably have them in your fstab too:
according to the fstab man page, these device id'd are useful when you automount removable devices, so that they will always be mounted to the same directory based on their id.
check for yourself in
```
man fstab
```
and search for uuid
```
/uuid (Enter)
```
hope this helps
and, of course, peace :)

---

