---
title: "Shrink ext3 Partition?"
date: 2005-10-30
forum: General Help
---

### Post by Donnut on 2005-10-30
Can I shrink an ext3 partition to make a Fat32 Windows partition?  I have a 40gb that has an ext3, a linux swap, and an extended.  But I can't make a new partition...

---

### Post by suRoot on 2005-10-30
Probably the easiest thing to do would be to download the Ultimate Boot CD ([http://www.ubcd4win.com/downloads.htm]("http://www.ubcd4win.com/downloads.htm")) which - I think - includes tools to resize partitions.

If not, you could do it from within Linux, but it would require (a little) more work.  Either boot up in single user mode or download a live linux cd & boot from that.  The point is that you'll need to be able to unmount the partition.  If you want to resize your boot partition, you won't be able to do that while running the OS.  If it's not the boot partition, you could just unmount it & resize.  Do some reading on tune2fs & parted.  If you feel comfortable trying it after reading, then you can give it a shot.

The easiest thing would be to grab something like partition magic - and as best I remember the ultimate boot cd comes with a copy, or something very similar.

Good luck!

---

### Post by matthewv on 2005-10-30
Most people with ubuntu will already have the ubuntu live cd. This includes GParted, which is a partition magic clone. I'm not sure if it can resize ext3 though. It is based upon the same libraries as the ones used by the ultimate boot cd.

---

### Post by suRoot on 2005-10-30
[QUOTE=matthewv]Most people with ubuntu will already have the ubuntu live cd. This includes GParted, which is a partition magic clone. I'm not sure if it can resize ext3 though. It is based upon the same libraries as the ones used by the ultimate boot cd.[/QUOTE]

gparted can do it.

---

### Post by Donnut on 2005-10-30
Thanks for your input guys, ill try that.

---

