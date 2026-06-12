---
title: "Fixing ntfs partition"
date: 2008-05-28
forum: General Help
---

### Post by dgm3808 on 2008-05-28
Hi everybody, I'm from Argentina, so please forgive if I make any kind of mistake... my english isn't really perfect, you know.

The thing is I have a dual-boot computer, with Ubuntu and Windows XP currently installed, but yesterday my PC just shutted down automatically, and next thing I knew, I just couldn't run Windows anymore. It kind of shuts my computer down whenever I try to boot, or it might run for a minute or two and then shutdown... or that nasty blue-screen-of-the-death might appear while booting.

Ubuntu works perfectly :lolflag:, even though when I boot it, it makes a partition-check and I get this log:

```

Log of fsck -C3 -R -A -a 
Wed May 28 01:38:31 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda2: clean, 44/52208 files, 67489/208812 blocks
fsck.ext3: Unable to resolve 'UUID=db2e5165-b924-48e5-aa04-ade57c5e0f5f'
fsck died with exit status 8

Wed May 28 01:38:31 2008
----------------

```

It'll be really nice to have both of my OS able to run :P... so I tried to fix my NTFS partition from here, but nothing worked.

Doing a little research, I realised I could try to force the mount of the NTFS partition, using:

```
sudo ntfs-3g -o force,rw /dev/sda1 /media/windows
```

or (can't remember)

```
sudo mount -t ntfs-3g -o force,rw /dev/sda1 /media/windows
```

This way I am able to browse the files from that ntfs partition. However, when I tried to schedule a NTFS consistency check with the unit unmounted, using:

```
sudo umount /media/windows
sudo ntfsfix /dev/sda1
```

I get this message:

```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.

```

Well, I think that's about it... again, sorry for my english (and linux :P) mistakes, and thank you all...

---

### Post by pointone on 2008-05-28
Please post your "/etc/fstab" and the output of running "blkid".

---

### Post by dgm3808 on 2008-05-28
Actually, I was able to solve this by myself...

Thanks anyway! :)

---

