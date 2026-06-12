---
title: "Question about default partition structure"
date: 2014-08-28
forum: General Help
---

### Post by project722 on 2014-08-28
When I originally setup Ubuntu this was my default partition layout. I noticed that sda2 and 5 share the same space/blocks/sectors, etc. Why is that? Does swap space require its own separate dedicated partition?

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    32505855    16251904   83  Linux
/dev/sda2        32507902    33552383      522241    5  Extended
/dev/sda5        32509950    33552383      521217   82  Linux swap / Solaris

---

### Post by sudodus on 2014-08-28
/dev/sda2 is an extended partition, a container for other partitions (logical partitions).

The classical MSDOS partition table allows only four partitions (primary partitions). Then someone invented the extended partition to allow making more partitions. And this is used in the default partition layout. If there is no other partition, that you want to keep during the installation, the root partition in a primary partition and the swap partition is a logical partition inside the extended partition).

[COLOR=#696969]If you want dual boot with Windows, it will be different. In some computers Windows is already occupying four partitions, so you must remove one to make it possible to create an extended partition ...[/COLOR]

---

### Post by grahammechanical on 2014-08-28
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by project722 on 2014-08-28
Thanks sudodus!

---

### Post by sudodus on 2014-08-28
You are welcome :-)

---

