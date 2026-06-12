---
title: "Write bit pattern to usused parts of the disk.."
date: 2007-04-16
forum: General Help
---

### Post by bushtor on 2007-04-16
Hi,

I have just installed ubuntu on an old disk.  This disk might have contained some sensitive data previously and I would like to overwrite all *unused* parts of the disk with some bit/byte patterns.

How do I do this most elegantly.  I have not installed the desktop version, only the 6.06 server.

Thanks for info on what to do in this case ;-)

Thanks

/tor

---

### Post by rufius on 2007-04-16
I wouldn't recommend the bit pattern as it wouldn't be that safe just because of how the system flushes and the technology of recovering data thats been written over. On that note, I do know of a utility that you can use.

There's a GNU tool called "shred" that can be used on files or devices. Typically you wouldn't use it on files since it doesn't work well with journalised file systems. If you shred a device there won't be any hope of recovering data and you can safely install the system.

I believe the tool is part of the core of the GNU utilities so it should be available on the Ubuntu boot disk. You should be able to boot the Ubuntu install cd, and run this command on the disk:
```
shred --verbose /dev/<device>
```

You can then create your partitions and install.

---

