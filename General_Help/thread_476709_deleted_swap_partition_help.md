---
title: "deleted swap partition help"
date: 2007-06-17
forum: General Help
---

### Post by Jay_in_TN on 2007-06-17
I deleted my swap file partition and re-created it using a windows partition manager (while working in windows on my primary HD). Now when trying to boot Feisty (on my other HD) it says apt-get missing and wont boot. I am assuming it needs a file that is gone from the swap partition. Can I fix this without a Feisty reinstall?
Thanks,
Jay

---

### Post by 5-HT on 2007-06-17
Missing apt shouldn't have anything to do with the swap partition*.
After you create the partition, you'll need to set up the swap area:
```
sudo mkswap /dev/{swap_partition}   *without the {}
sudo swapon -a
```as well as making sure the swap entry in /etc/fstab points to the correct partition.
Can you boot into recovery mode at all?
If not, you could boot up a live CD, make sure your swap is set up, and chroot into your install to reinstall apt if necessary.

cheers,


*Note: Did you create a swap partition, or swap file?

---

### Post by s.deleeuw on 2007-06-17
These lines are from my /etc/fstab:

```
# /dev/sda7
UUID=b6c762ce-524e-4a26-ae51-1b4821765c93 none            swap    sw            
```

Since Edgy, partitions are referenced to by this UUID. When you recreate the swap partition, the UUID is changed as well, making your system unbootable. You will have to update the UUID, or easier, replace it by /dev/sda?, like in good old times.

I don't understand why the UUID's are introduced in the first place. Every change in my partition-table, or even a format makes my system unbootable. And provided software like GParted doesn't update my /etc/fstab automaticly. I think things are more complicated this way...

---

### Post by 5-HT on 2007-06-17
If you're going the UUID route for your fstab, you can check to see if it's the right one by:
```
ls -l /dev/disk/by-uuid
```

---

### Post by Jay_in_TN on 2007-06-17
Thanks for the answers everyone. I got impatient and just reinstalled Feisty as it was a new install anyway.
Good information if this happens in the future or if someone else needs the thread.
Jay

---

### Post by LinuX-M@n1@k on 2008-06-01
Thanks all! I needed it ;).

---

