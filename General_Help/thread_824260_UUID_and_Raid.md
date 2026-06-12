---
title: "UUID and Raid"
date: 2008-06-09
forum: General Help
---

### Post by RaygionsSumta on 2008-06-09
I am in the process of setting up a software RAID 5 array on a fresh install of Hardy Heron.  I have wiped and reinstalled several times as I experiment, sometimes with remarkable results.  UUIDs are making me nervous.  The boot drive is a 2.5" 40GB Samsung PATA.  At installation time it is designated as sda1 (swap sda5).  Once the OS is installed, I fdisk the four Samsung SpinPoint 400GB SATA drives, which become sdb1, sdc1, sdd1, and sde1.  No surprises so far.  

Now I am testing, because I have a suspicion, from a prior install, that either a drive or a cable is bad.  As part of that process, I reboot. And when the system comes back up, the SATA drives are sda[1-4] and the PATA drive is  sde1 with a swap of sde5.

UUIDs are all well and good, but mdadm appears to depend on device names.  The whole shifting names thing has me nervous.  What happens when... it changes on another reboot?  Or if I add a drive?  Or if I drop the PATA for another SATA as the boot?  Or I grow the array?

Am I fretting for nothing?

---

### Post by Unix_Slayer on 2008-06-09
> **RaygionsSumta said:**
> 

UUIDs are all well and good, but mdadm appears to depend on device names.  The whole shifting names thing has me nervous.  What happens when... it changes on another reboot?  Or if I add a drive?  Or if I drop the PATA for another SATA as the boot?  Or I grow the array?

Am I fretting for nothing?

There is a program you can us in linux for disc array5. I'm not sure of the name of it at this time, but I was working on that same thing. I have two disc arrays, with 4 terabytes each. I need to transfer my stuff off of a set, from Windows. Then I can re-do it in Ubuuntu.

---

### Post by atoponce on 2008-06-09
How are the partition IDs on your partitions?  Seeing as though you are using mdadm with disk partitions, it's critical that the partitions be marked as 'fd   Linux raid auto", or there is no guarantee in the rebuilding of the array, or it's consistent nature.  You can change the partition's ID with fdisk.

---

### Post by RaygionsSumta on 2008-06-09
> **atoponce said:**
> How are the partition IDs on your partitions?  Seeing as though you are using mdadm with disk partitions, it's critical that the partitions be marked as 'fd   Linux raid auto", or there is no guarantee in the rebuilding of the array, or it's consistent nature.  You can change the partition's ID with fdisk.

There is one partition per drive that is going into the array, and the drive has been typed fd. No problems there. I am concerned about the effects of the shifting device designations that I am observing (e.g. /dev/sda1 to /dev/sdb1) on any array I might build.

joe

---

### Post by Unix_Slayer on 2008-06-10
Are you using mdadm, and dmraid?

---

### Post by fjgaude on 2008-06-10
Say, mdamd depends on superblocks of each drive to know how to assemble an array. It doesn't care about names or the /dev designation.

You can move the array physcially to another Ubuntu computer and simply do, after making sure mdadm is on the computer, a

```
sudo mdadm --assemble --scan
```

and the array is up and running.

I've used the same array for years, many OS and hardware changes, without incident.

---

### Post by Unix_Slayer on 2008-06-11
> **fjgaude said:**
> Say, mdamd depends on superblocks of each drive to know how to assemble an array. It doesn't care about names or the /dev designation.

You can move the array physcially to another Ubuntu computer and simply do, after making sure mdadm is on the computer, a

```
sudo mdadm --assemble --scan
```

and the array is up and running.

I've used the same array for years, many OS and hardware changes, without incident.


I'm still trying to get my 10 terabytes working.

---

### Post by fjgaude on 2008-06-11
You using the raid created by your BIOS, eh? From there in Ubuntu you will then have to use dmraid, not mdadm.

---

### Post by Unix_Slayer on 2008-06-11
> **fjgaude said:**
> You using the raid created by your BIOS, eh? From there in Ubuntu you will then have to use dmraid, not mdadm.

The Silicon Image card sees it in the card bios when it boots. I tried dmraid -ay. It sees it as a drive [sdg]. I can't decipher whats going on with it as yet.

---

### Post by heddhunter on 2008-06-11
> **atoponce said:**
> How are the partition IDs on your partitions?  Seeing as though you are using mdadm with disk partitions, it's critical that the partitions be marked as 'fd   Linux raid auto", or there is no guarantee in the rebuilding of the array, or it's consistent nature.  You can change the partition's ID with fdisk.
I've been running an mdadm assembled array with all the partitions set to type Linux.  It seems to work perfectly well.  Is that going to bite me later?  If I change the partition type, will I have to reformat and recreate the array or will I be able to retain all the data?

---

### Post by Unix_Slayer on 2008-06-11
> **heddhunter said:**
> I've been running an mdadm assembled array with all the partitions set to type Linux.  It seems to work perfectly well.  Is that going to bite me later?  If I change the partition type, will I have to reformat and recreate the array or will I be able to retain all the data?

That's what I am pondering. I would like to keep my raids just the way they are. I can read ntfs drives in linux.

---

