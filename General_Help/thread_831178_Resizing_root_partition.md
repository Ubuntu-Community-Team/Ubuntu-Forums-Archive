---
title: "Resizing root partition"
date: 2008-06-16
forum: General Help
---

### Post by cyclonedr on 2008-06-16
Hi all,
  When I partitioned Ubuntu before installation, I made my root, / partition to small, 4GB.  I've also a home partition with 14Gb free.  I thought that only system files would install to the root, but it seems whenever I install something, the root space gets used up.  I went into GParted to resize my root partition, and it won't let me make it any bigger, even though there is about 12GB of unallocated free space available.  Does having it in an extended partition make this so?  Can I make it so that stuff will be installed on my main home partition?  Thanks for any tips

---

### Post by rune0077 on 2008-06-16
> **cyclonedr said:**
> Hi all,
  When I partitioned Ubuntu before installation, I made my root, / partition to small, 4GB.  I've also a home partition with 14Gb free.  I thought that only system files would install to the root, but it seems whenever I install something, the root space gets used up.  I went into GParted to resize my root partition, and it won't let me make it any bigger, even though there is about 12GB of unallocated free space available.  Does having it in an extended partition make this so?  Can I make it so that stuff will be installed on my main home partition?  Thanks for any tips

It's because you can't resize a drive that is mounted. You'll need the gparted live-cd (google it, download it, burn it and boot it :)) Then you should be able to do it.

---

### Post by Hozza on 2008-06-16
To resize a root partition you could use gparted on a live boot CD 8)

---

### Post by cyclonedr on 2008-06-16
I should have been more specific, I did boot from the live Cd while trying to make the root partition bigger.  My current setup is I have just a little bigger than a 5Gb extended partition, with 4GB for root and 1Gb for swap. There is about 257MB unallocated.  Outside of the extended partition I've a 14GB home partition.  I also have 2 other partitions, one for backup, and one for storage.  I even with those I have about 12Gb for space.  I'm wondering why it won't let me resize even with the extra 257mb in the ext'd partition.

---

### Post by geirha on 2008-06-16
The ubuntu liveCD might mount the swap partition on your harddrive. If it has, you'll need to unmount it by right-clicking it in gparted, and select unmount.

If that's not it, then what does your partition table look like? ```
sudo fdisk -l
```

---

### Post by uidb4056 on 2008-06-16
You will need to have this 12 GB unallocated space just at begin or end of your extended partition (you may need to move other partitions for it) then increase the extended partition and then increase your root partition inside (you will need again the unallocated space at side of your root partition)

---

### Post by cyclonedr on 2008-06-16
I'm sorry for failing to make clear, I was in the GParted live Cd.

---

### Post by rune0077 on 2008-06-16
> **cyclonedr said:**
> I'm sorry for failing to make clear, I was in the GParted live Cd.

Okay, then you probably need to move the free space next to the partition you want to make larger. I haven't used gparted for a while, but isn't their an option that let's you move around the free space?

---

### Post by avtolle on 2008-06-16
An observation; linux only allows adding space to an existing partition "at the end". Thus, if the /swap or the /home partition is shown as being next to the / (root) partition, while you have empty space on the hdd, it isn't where it needs to be. Shrinking the /swap or /home partition won't do you any good, as the space created will be at the end of the partition which has been shrunk. So, what to do? If the /swap partition is the one next to /, then delete it, reformat it, and then enlarge / to include this newly made space, after which you would create a new /swap in the 12 mb space I understand is available. Other option is to back up your /home, reformat both the swap and home, resize the / partition, then create new /swap and /home partitions.

---

