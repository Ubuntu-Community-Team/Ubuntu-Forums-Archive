---
title: "Mixing and matching mdadm, lvm2 MBR and GPT on RAID arrays."
date: 2022-02-07
forum: General Help
---

### Post by rsteinmetz70112 on 2022-02-07
I have some old arrays that have been continuously updated for many years. They have been transfered to new hardware more that once. The arrays were originally set up using MBR partition tables with lvm2 on top on mdadm. I'd like to move them to newer hardware with lvm2 only on gpt partition tables. I know that mdadm and lvm2 use the same underlying code. It seems to me that they should be compatible. I don't see any reason a properly set up GPT partition could not be included in an array with an MBR partition.

Is there any chance this will work or am I crazy?

I envision something like this;
[LIST=1]
[*]Set up new drive with a GPT partition.
[*]Set up an empty  lvm2 array on the drive.
[*]Remove an existing drive from an existing lvm2 volume from an existing mdadm array
[*]Add the volume to the lvm2 array and sync. 
[/LIST]

---

### Post by MAFoElffen on 2022-02-07
mdadm does not care if the drives are MBR or GPT... but remember your hierarchy... Think of it just like Russian Nested Dolls

A) physical disks
A.1 Partitions
A.1.a. mdadm RAID array is group of partitions... that creates an array that appears as a storage space...
A.1.a.x01 is LVM2 PV extent... which is within LVM type partitions within that mdadm array (of type LVM)... Then within that you have LVM LG. Within that LVM LV. Within that, the filesystem...

To setup that up without mdadm RAID, you just skip level A.1.a, by creating partitions of type LVM and adding them as LVM PV extents... What I like about a setup like that, is that you can easily add and remove PV extents from/to drives, while running/hot.

Does that make sense to you, or should I explain that differently?

Note1: Although it is 'possible' to declare a raw drive as a mdadm member, my experience shows me, that "that" is not always a good idea, and can cause problems. It also cuts down my options and flexibility. I always avoid that.

Note2: Although it is possible to mix media, LVM does not care if that LVM type partition (hex code 8e, LVM flag) is on mdadm or a partition straight on the physical disk. You can add whatever of that to PV extents... but you add confusing complexity to anyone trying to figure out what you did and why...

---

### Post by rsteinmetz70112 on 2022-02-07
I understand about partitions. I was wondering if I create an lvm partition can that be added to a mdadm array? When I built the original arrays about 15 years ago I don't believe lvm had the ability to do RAID.

Maybe this is clearer

Existing Drive
[LIST]
[*]/dev/sda - MBR partition table
[*]/dev/sda1 mdadm array member with lvm 
[/LIST]

New Drive 1
[LIST]
[*]/dev/sdb GPT partition Table
[*]/dev/sdb1 EFI partition
[*]/dev/sdb2 LVM partition
[/LIST]

New Drive 2
[LIST]
[*]/dev/sdc GPT partition Table
[*]/dev/sdc1 EFI Partition
[*]/dev/sdc2 LVM partition
[/LIST]

/dev/md0 RAID 1 array with /dev/sda1 /dev/sdb2 
If that works I could remove /dev/sda1 from /dev/md0 and add new partition /dev/sdc2

I haven't worked with lvm arrays yet, so I'm a little fuzzy.

---

### Post by MAFoElffen on 2022-02-07
Well, sort of... It depends on the RAID Type and how you have the LVM2 PV extents added. 

For LVM2, you can move PV extents from a disk, to remove the disk... You shrink the filesyste, lv, vg. then move the PV data off that disk to rest of the PV pool... then remove that disk from the extents. But if you have it inside of a RAID array, it sees that Array as one PV extent. Logically, it sounds like it might work, by removing the member from the Array, because it will shift everything...

But I would test it on a VM first to see if the logic is sound. That is usually what I do to confirm something will work, before i try it live... That way I can work through the commands, and what has to happen when, with no surprises.

See attachment... That is Ubuntu RAID-on-root, RAID5 with sync'ed EFI partitions...

---

### Post by rsteinmetz70112 on 2022-02-07
With my existing RAID1 arrays. They are all lvm on mdadm so lvm2 sees the md as a single disk. You can remove a disk from an md and add another one then use mdadm tools to resize the md and then lvm to change the vg lv. That's been the way I expanded arrays before . fail a disk add an new one with a partition to the array sync it then do the same thing with teh other disks. All of my arrays are RAID 1, I'm looking for protection against hardware failure and downtime since I'm not always at the site.

I guess the other way to do it would be build a completely new array and copy everything to it.

---

### Post by MAFoElffen on 2022-02-08
Or mirrors within LVM2... You did mention thinking about that. Without RAID altogether.

Why do I mention that? I used to do hardware RAID on everything.Then mdadm... Now? I support RAID, but for my own, I use LVM2 and/or ZFS.

RAID is not a replacement for a backup and recovery plan. I have learned that in my backups, with them and a new install, I can be back up to a specific point in time very much faster than trying to rebuild/resync a RAID array. (So without RAID) That process in itself can take a very long time... where the goal is "uptime." That is just the real world reality. I have to pick my battles, where to focus my efforts and priorities.

I am not against mdadm. I still support it... To the point where I was the Project lead on mdadm-gui, but lost interest on that as I saw trends and technology change and evolve over time..

I am leaning back to that with Gen 5 NVMe Datacenter drives... but that is another perspective that needs exploring.

---

### Post by rsteinmetz70112 on 2022-02-08
I have backups both local and remote. I am mostly interested in keeping the computers running in the event of a hardware failure until I can get there and physically replace a drive.

---

