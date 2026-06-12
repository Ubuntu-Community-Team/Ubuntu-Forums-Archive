---
title: "Can't boot after adding partition"
date: 2019-02-08
forum: General Help
---

### Post by kristijanog on 2019-02-08
[COLOR=#242729][FONT=Arial]I'm hosting a LimeSurvey server using a Ubuntu VM. After some time I needed to add another partition adding 50GB to an existim LVM group. After adding the partition the structure looked like this:
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]sda 100G[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]&#9500;&#9472;sda1 ext2 243M /boot[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
&#9500;&#9472;sda2 1K[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
&#9500;&#9472;sda3 LVM2_member 50G[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
&#9474; &#9492;&#9472;limesurvey--vg-root (dm-0) ext4 99.8G /[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
&#9492;&#9472;sda5 LVM2_member 49.8G[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
&#9492;&#9472;limesurvey--vg-root (dm-0) ext4 99.8G
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]sda3 is the new added partition. All functioned fine until I **restarted** the VM after 3 months of usage:[/FONT][/COLOR]

Gave up waiting for root device
ALERT! /dev/mapper/limesurvey--vg-root does not exist. Dropping to a shell!

[COLOR=#242729][FONT=Arial]So, it doesn't boot to ubuntu but stays in initramfsr. I can't use any backup for booting up except the ones before the partitioning.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This is how I did the partitioning: 
[IMG]https://i.imgur.com/IeNL52r.png[/IMG]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][IMG]https://i.imgur.com/uAt1Lgu.png[/IMG]

Because of the partition adding the swap partition was removed so I added an additional swap file using this instructions:[/FONT][/COLOR][INDENT][FONT=inherit]create a swap partition[/FONT]

[LIST=1]
[*]Create an empty file (1K * 4M = 4 GiB).
[/LIST]
[FONT=inherit]sudo mkdir -v /var/cache/swap[/FONT]
[FONT=inherit]cd /var/cache/swap[/FONT]
[FONT=inherit]sudo dd if=/dev/zero of=swapfile bs=1K count=4M[/FONT]
[FONT=inherit]sudo chmod 600 swapfile[/FONT]

[LIST=1]
[*]Convert newly created file into a swap space file.
[/LIST]
[FONT=inherit]sudo mkswap swapfile[/FONT]

[LIST=1]
[*]Enable file for paging and swapping.
[/LIST]
[FONT=inherit]sudo swapon swapfile[/FONT]
[FONT=inherit]Verify by: swapon -s or top:[/FONT]
[FONT=inherit]top -bn1 | grep -i swap[/FONT]
[FONT=inherit]To disable, use sudo swapoff swapfile command.[/FONT]

[LIST=1]
[*]Add it into fstab file to make it persistent on the next system boot.
[/LIST]
[FONT=inherit]echo "/var/cache/swap/swapfile none swap sw 0 0" | sudo tee -a /etc/fstab[/FONT]

[LIST=1]
[*]Re-test swap file on startup by:
[/LIST]
[FONT=inherit]sudo swapoff swapfile[/FONT]
[FONT=inherit]sudo swapon -va[/FONT]
[/INDENT]
[COLOR=#242729][FONT=Arial]

Could anyone shed some light why after the restart of my VM, while it worked perfectly fine for 3 months, the partition broke down?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thank you![/FONT][/COLOR]

---

### Post by dmnur on 2019-02-08
**fdisk -l /dev/sda** output would be helpful.

My guess is that you were creating partitions in this order:
sda1 > sda2 > sda5 > sda3

So initially it was:
sda1 is primary
sda2 is extended
sda5 is logical (logical partition numbers are always 5+)

MBR partition table is limited to 4 partitions, that's why they came up with the so-called extended partition.
The extended partition is actually a primary partition that is used to store more partition records (so-called logical partitions).

Then you probably have resized the VM disk, and the newly added space was appended to end of the disk. 100G total now. So, the extended partition still holds 50G. You create the new partition, but it cannot be added to your extended partition: no space left there. So the partitioning tool create a primary partition, giving it number 3.

What you have then is the situation when partition numbers don't match their physical order:
sda1 > sda2 > sda3 > sda5
are actually physically ordered as
sda1 > sda2 > sda5 > sda3

Facilities used to mount LVM at boot probably don't expect that and fail.

Fixing the logical order is not too hard: you just need to save **fdisk -l** output somewhere, delete wrongly numbered partitions and recreate them at the same sector positions they were ***and*** with the same types.

You'd probably want something like this:
sda1 is primary, 250M, /boot
sda2 is extended, 100G
sda5 is logical, 50G, LVM1
sda6 is logical, 50G, LVM2

For future VMs it would be better not to create a new partition for the newly added space, but just use **pvresize** to extend the size of the last partition:
sda1 primary 250M /boot, sda2 primary 50G LVM
to
sda1 primary 250M /boot, sda2 primary 50G LVM, free 50G
to
sda1 primary 250M /boot, sda2 primary 100G LVM

---

### Post by kristijanog on 2019-02-08
Dmnur, thank you for your precise and knowledgeable answer. I can understand it clearly although I'm a Linux beginner.

I would love to give you the **fdisk -l /dev/sda** output but I'm having problem doing that from the the initramfsr:

[IMG]https://i.imgur.com/xHQY1sy.png[/IMG]

Clearly I'm over my head in this but I'm ready to learn if you have the time to guide me through the process. Thank you kindly!

---

### Post by dmnur on 2019-02-08
You're welcome, **kristijanog**. :)

> **kristijanog said:**
> I would love to give you the **fdisk -l /dev/sda** output but I'm having problem doing that from the the initramfsr

Yes, you won't be able to do this from initramfs, it's very minimalistic. I guess your VM is hosted by some VPS provider. They probably allow you to mount ISO images and boot from them.
Boot from some kind of LiveCD, e.g. GParted Live or Ubuntu Desktop, and run the command from there.

---

### Post by kristijanog on 2019-02-09
Thanks a bunch! :)

This is my fdisk -l output:

[IMG]https://i.imgur.com/GzJaz1e.png[/IMG]

The Extended (sda2) size confuses me. Shouldn't it be 100G considering the two LVM's, each with 50G space? If it should be like that (100G), what steps should I take to recreate the partitions after deleting them and recreating them (sda2, sda5 and sda3 -> sda2, sda5, sda6)? Should I, while recreating the sda2 partition, put the start at 501758 but the end at 209715199 where the newly created sda3 ends? Or am I not understanding the logic behind extended and LVM partitions?

---

### Post by dmnur on 2019-02-09
The extended partition must be of the size of all partitions it holds. Actually, its real size is just 1 KiB, as you could see in the **lsblk** output. The size the **fdisk** output shows is how much space that extended partition *manages*.

First of all, back up your current partition table, just in case.
```

sudo dd if=/dev/sda of=sda-mbr.bin bs=512 count=1

```

Save this **sda-mbr.bin** somewhere where you could get it later, like cloud storage.

So, in your case you should do the following (I recommend using **fdisk** for partitioning, much easier to be precise in sector numbers):
[LIST=1]
[*] Delete partitions 2, 3, 5. 
[*] Create a primary partition that starts at sector 501760 and ends at sector 104855551. Make sure its type is **8e** (Linux LVM) (use the **t** command in **fdisk**). This will be your old sda5, new sda2.
[*] Create another primary partition: start 104900000, end 209715199. Again, make sure its type is **8e** (Linux LVM). This will be your old sda3, new sda3.
[/LIST]

In this case you won't need the extended partition and logical partitions at all. Be careful though: only one slot remains! If you don't want to create more partitions, that's fine. As I said earlier, you won't need to create new partitions for extending your logical volumes. If, however, you need more, use this last slot to create the extended partition. Then, if you resize your VM disk, you would need to resize your extended partition for it to manage all new available space.

---

### Post by kristijanog on 2019-02-09
I'll try this method this afternoon and tell you the results.

Spasibo dmnur!

Kristijan

---

### Post by kristijanog on 2019-02-09
Hi,

I followed your instructions but I get te same error while booting my Ubuntu VM. This is the current situation:

[IMG]https://i.imgur.com/HFYj2xx.png[/IMG]

[IMG]https://i.imgur.com/BwTKTin.png[/IMG]


I've made a backup of my VM prior doing this so nothing is lost. Is this maybe a LVM label problem?

Thank you, I'm really novice at this :) After the problem is solved I'm getting myself a good Linux book before messing with partitions in the future.

---

### Post by dmnur on 2019-02-09
From the LiveCD, show the output of **pvs**, **vgs** and **lvs** commands.

Also try to mount your logical volume and let's see what happens:
```
sudo mount /dev/mapper/limesurvey-vg-root /mnt
```

Oh. I've actually noticed something else. Well, first things first.

---

### Post by kristijanog on 2019-02-09
pvs, vgs and lvs doesn't give me any output and I didn't succeed to mount :(
[IMG]https://i.imgur.com/KJADVeJ.png[/IMG]

Does the virtual group even exist in this case?

---

### Post by dmnur on 2019-02-09
Run these, then try again:
```

sudo systemctl start lvm2-lvmetad
sudo pvscan

```

---

### Post by kristijanog on 2019-02-09
[IMG]https://i.imgur.com/k00YTWl.png[/IMG]

---

### Post by dmnur on 2019-02-09
OK, let's try this:
```

sudo pvs -a
sudo vgscan -vvvv

```

The output of the second command will be very long, use something like this to upload it and get a short link (of course make sure you have working network connection):
```
sudo vgscan -vvvv | nc termbin.com 9999
```
You can then open this link locally from your computer and save the output to a file, then attach this file to your forum message.

**UPD:** also try booting from Ubuntu Desktop ISO, I'm not sure if GParted Live handles LVM well.

**UPD2:** the problem is solved, I'll describe the solution later.

---

