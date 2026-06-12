---
title: "Can I share swap space between distros?"
date: 2023-01-13
forum: General Help
---

### Post by Jason Spaceman on 2023-01-13
I have a 2TB SSD drive that I plan on partitioning, giving one third to Ubuntu, one third to Arch Linux, and one third to Alpine Linux.

Rather than create a swap space for each install, could I not create a single swap space formatted as 'Linux swap' and share that between all three?  I'm only ever going to be running one distro at a time, so only one distro will be writing to swap at any given time.


Thanks,
Jason

---

### Post by guiverc on 2023-01-13
I have many boxes with multiple installs (*including the current box I'm using now*), and I have **all** systems share my swap partition.

In some installs I use both *swapfiles* and the shared *swap partition*, whilst it's not as efficient as using only *swap partition* (*in my opinion*), it allows me to get additional functionality that I couldn't get otherwise.

You **can't** *hibernate *a system, and then boot another when using *shared swap partition*, though that's when I can run a *script* that disables the use of *swap partition* after mounting *swapfile*, thus meaning my *shared swap partition* is not being used, allowing me to boot/use another system using my default *shared swap partition*.

There can also be complications relating to *encryption*, but you didn't mention encryption so I've avoided the complexities ofencryption in what I've written.FYI:  I've not mentioned OSes, but I'm thinking of GNU/Linux here, and running Debian currently, but my shared systems on this box are all Ubuntu (*four different installs on this box*).  My other boxes also include OpenSuSE, Fedora etc.. plus of course Ubuntu.

FYI:  I don't share data partitions; used to, but decided it wasn't worth it.  I share only specific directories.

---

### Post by TheFu on 2023-01-14
Yes, but could I convince you to use virtual machines?  Having access to multiple OSes concurrently opens all sorts of learning up.  Plus, having VMs lets us try things with nearly zero risks.

---

### Post by The Cog on 2023-01-14
Beware that the installer **always** re-formats the swap partition, and this changes the swap partition's UUID. This means the other distros all lose their swap partition, and you have to manually edit their fstab to get swap working again.

---

### Post by guiverc on 2023-01-14
I perform QA-test installs regularly on dual boot boxes such as I'm using now, and I don't expect the *swap* to be re-formatted on re-install, my current OS has access to the *swap partition*, and the only thing I need to correct, is the order of `grub` using `grub-install` on re-install of a system  (*ie. returning the grub back to the owner it was before a system is re-installed*).

Most of my QA currently is with Lubuntu, thus `calamares` which will re-use a *swap* partition, but I'd expect the same for `ubiquity` installs as well  (Ubuntu has many installers, I rarely use `subiquity` so couldn't speak to it, wouldn't be surprised if the *canary* installer (`ubiquity` replacement) did format but I don't know (*most of my installs with it have been full disk*), the *di* installer is really *deprecated* so unless installing an old system I'd not expect many to use it (*and wouldn't be surprised if that formatted; I don't know*).

I have had `ubiquity` installs re-format the *swap *though; but I don't recall what triggered it.  I disagree with the *always* though (*as for formatting on re-install - but it's possible with some options*)

---

### Post by TheFu on 2023-01-14
> **The Cog said:**
> Beware that the installer **always** re-formats the swap partition, and this changes the swap partition's UUID. This means the other distros all lose their swap partition, and you have to manually edit their fstab to get swap working again.

If you don't mount using the UUID, rather using either the LVM VG-LV path or use the LABEL, then the changing UUIDs can be avoided.
Here's the fstab for one of my systems, using LVM for the swap:
```
/dev/vg00/swap                             none      swap sw 0 0
```
vg00 is the VG name.
swap is the LV name.

Any of the links under /dev/disk/ can be used, the trick is to not use any that change. These are some of the choices:
```
$ ls /dev/disk/
by-id/  by-label/  by-partlabel/  by-partuuid/  by-path/  by-uuid/
```
By-Path/ shouldn't change unless the physical connections are moved - like moving the SATA port.  I find mounting using UUIDs unhelpful when we have human-usable alternatives that actually make sense, not just something random.  We aren't looking for passphrases.

---

### Post by #&amp;thj^% on 2023-01-14
> **TheFu said:**
>   I find mounting using UUIDs unhelpful when we have human-usable alternatives that actually make sense, not just something random.  We aren't looking for passphrases.
+1
just another variation to show:
```
cat /proc/swaps
Filename				Type		Size		Used	Priority
/dev/dm-0                               partition	7999484		0	-2
/dev/nvme0n1p2                          partition	8196092		472832	-
```
I seem to have another option that shows:
```
ls /dev/disk/
**_by-diskseq _** by-id  by-label  by-partlabel  by-partuuid  by-path  by-uuid

```
swaps in use:
```
sudo swapon 
NAME           TYPE      SIZE   USED PRIO
/dev/dm-0      partition 7.6G     0B   -2
/dev/nvme0n1p2 partition 7.8G 457.8M   -3

```
formatted as:
```
inxi -p | grep btrfs
  ID-1: / size: 237.02 GiB used: 23.98 GiB (10.1%) fs: btrfs dev: /dev/dm-2
  ID-2: /boot size: 977 MiB used: 105.6 MiB (10.8%) fs: btrfs dev: /dev/sdb2

```

---

### Post by TheFu on 2023-01-14
> **1fallen said:**
>  
I seem to have another option that shows:
```
ls /dev/disk/
**_by-diskseq _** by-id  by-label  by-partlabel  by-partuuid  by-path  by-uuid

```

I'm on a 5.4 kernel across almost all my production systems.
1 system is on 5.15 and it has /dev/disk/by-dname/ too.  That appears to be LVM names but only for NVMe, not any SATA connected devices. Hummmm.
```
lrwxrwxrwx 1 root root  10 Jan  9 15:18 vg00-home -> ../../dm-7
lrwxrwxrwx 1 root root  10 Jan  9 15:18 vg00-root--00 -> ../../dm-5
lrwxrwxrwx 1 root root  10 Jan  9 15:18 vg00-swap -> ../../dm-4
lrwxrwxrwx 1 root root  10 Jan  9 15:18 vg00-var -> ../../dm-6
```
I have lots of other VGs and LVs on that system, which aren't showing up in that by-dname directory.

Lots of viable options, instead of using UUIDs. Guess that's the real point.

---

### Post by #&amp;thj^% on 2023-01-14
> **TheFu said:**
> 
Lots of viable options, instead of using UUIDs. Guess that's the real point.

yes it was the point. :)

---

### Post by Tadaen_Sylvermane on 2023-01-14
> Beware that the installer **always** re-formats the swap partition,  and this changes the swap partition's UUID. This means the other distros  all lose their swap partition, and you have to manually edit their  fstab to get swap working again.

This is why lvm wins for me every single time. just mount via path. ```
/dev/main/swap none swap sw 0 0
```

---

### Post by MAFoElffen on 2023-01-15
> **Tadaen_Sylvermane said:**
> [COLOR=#a52a2a]This is [/COLOR][COLOR=#ff0000]why lvm wins for me[/COLOR] every single time. just mount via path. 

There are many reasons why a volume manager, such as LVM or ZFS is better than [COLOR=#a52a2a]a standard filesystem[/COLOR]... "This" <-- That you mentioned, is a mounting option, that TheFu, 1fallen, and others have mentioned... is Linux. 100's of ways to do the same thing. "This" is not specific solely to LVM. You understand that right? LOL

A lot of things in Linux are treated as a filesystem or path... It doesn't matter [COLOR=#ff0000]how[/COLOR] you point to it specifically (whether by label, UUID, path  to file/partition, etc) as long as you can point to it and it can be found.

---

### Post by TheFu on 2023-01-15
> **MAFoElffen said:**
>  
A lot of things in Linux are treated as a filesystem or path... It doesn't matter [COLOR=#ff0000]how[/COLOR] you point to it specifically (whether by label, UUID, path  to file/partition, etc) as long as you can point to it and it can be found.

The key is that the dynamically created links are identical between boots.  If they changed every time, it wouldn't be very useful.  They are symbolic links, which is a powerful idea Unix-like file systems have had for many, many, decades.  Other non-Unix OS file systems only recently added symbolic link support and I get the feeling very few people on that "other OS" know about them at all.

---

