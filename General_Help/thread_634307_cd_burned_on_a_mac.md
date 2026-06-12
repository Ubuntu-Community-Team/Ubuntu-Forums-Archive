---
title: "cd burned on a mac"
date: 2007-12-07
forum: General Help
---

### Post by Cirrocco on 2007-12-07
anyone know how to read the contents of a CD burned on an old Mac?

---

### Post by kidders on 2007-12-09
Hi there,

What filesystem was used? It might, for instance, be HFS or HFS+.

Assuming your optical drive is at /dev/cdrom, take a quick look at ...```
$ grep /dev/cdrom /etc/fstab
/dev/cdrom              /media/cdrom    udf,iso9660,hfsplus     noauto,ro,user  0 0
```If you want to mount a filesystem type other than those listed in your third option group ("udf,iso9660,hfsplus" in my example), you can do it with something like ...```
sudo mount -t hfsplus /dev/cdrom /mnt/mac_cd
```By manually specifying a filesystem type, you can override anything your /etc/fstab says about what format optical discs should be in.

As you can see, I've altered mine to try to mount DVDs, ISO9660 CDs, and Mac CDs (in that order). The other thing worth noting about what I've done is that the Mac part of a hybrid CD will never get mounted on my box, because "iso9660" and "hfsplus" are the wrong way around.

I'm no expert on "old" Macs (I've only started using them in recent years), so I'm not 100% sure the above will help you, but I *hope* it does!

---

**Edit:** If you can't find the right filesystem type to use, you could try dumping a little of your CD onto your hard disk, and asking Ubuntu what it is. For instance, if you did it with an Ubuntu boot CD, you might see...```
$ dd if=/dev/sr0 of=foo bs=4096 count=512
512+0 records in
512+0 records out
2097152 bytes (2.1 MB) copied, 1.16592 s, 1.8 MB/s
$ file foo
foo: [COLOR=DarkRed]**ISO 9660 CD-ROM filesystem data**[/COLOR] UDF filesystem data (unknown version, id 'NSR01') 'Ubuntu 7.10 amd64              ' (bootable)
```

---

