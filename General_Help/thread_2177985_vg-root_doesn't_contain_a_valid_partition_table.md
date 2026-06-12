---
title: "vg-root doesn't contain a valid partition table"
date: 2013-10-01
forum: General Help
---

### Post by James Wilde on 2013-10-01
Hi:

New installation of 13-04 64 bit.  I've done a search of the forums on the title without success.  Any easy way to recover from this error which came up when I was running fdisk to see how Ubuntu had partitioned the disk such as whether it had noted that I had created a swap partition and a big partition for home as well as the root partition.

TIA

James

---

### Post by steeldriver on 2013-10-01
Don't rely on fdisk for information about LVM volumes - it always gives that message, and it doesn't necessarily indicate anything is wrong. What actual problem are you having?

---

### Post by James Wilde on 2013-10-01
Thanks for your quick reply

No problems really, I hope.  I had a disk that was partitioned with three partitions on which I had the system (ca 20 GB partition) a swap partition and the rest of the disk which had originally been given over to /home.  There were some funny problems with the original installation, so I re-installed and wanted to see whether the installation had spotted the original structure.  Apparently it hadn't.

I was going to move /home to the big partition as it was before, and now I discover that my three partitions which were sda1, sda2 and sda3 are now suddenly sda1, sda2 and sda5.  Can this be a result of my having opted for LVM with this installation but not the previouos one?
 
Just tried to mount /dev/sda5 on /mnt to have a look at it and, if necessary format it and I get "mount: unknown filesystem type 'LVM2_member'".  Any suggestions?  I was planning to format it, copy my current home directory there and then mount it as /home.

James

---

### Post by steeldriver on 2013-10-01
Don't do that - likely sda5 is now a logical partition inside extended partition sda2, and contains the whole / filesystem on a single LVM2 logical volume. 

You can use other tools such as 'parted' to get a view of the current layout that (unlike fdisk) understands LVM, e.g.

```
sudo parted -l
```

---

### Post by James Wilde on 2013-10-01
Crap!  What a mess!

Thanks again for your input.  Since I'm not long down this road, nothing serious configured, I think I'll begin again and select my own partitions as I originally did.

---

