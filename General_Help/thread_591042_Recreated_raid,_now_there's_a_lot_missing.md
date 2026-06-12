---
title: "Recreated raid, now there's a lot missing"
date: 2007-10-25
forum: General Help
---

### Post by carpespasm on 2007-10-25
I upgraded to 7.10 earlier this week, and the whole thing went smoothly except for the software raid i set up disappeared. I used mdadm to originally create a RAID 1 with my two 500gb  SATA drives and am booting off a PATA drive. Last night I tried to recreate this and when I did mdadm noticed the two SATA drives were EXT2 and part of a RAID Array, which was comforting to see it recognize, but once it had made the md0 device and I mounted it, it seems like the only stuff on the array is VERY out of date. probably no more than a few weeks after I originally made the original setup about 3-4 months ago.

Does anyone have any idea what's going on here or if I can recover this loss? I've unmounted the device now to prevent anything from writing to it until I know what's going on, but I'm afraid that the damage is already done since the two drives have already synced.

Help.:(:confused:

---

### Post by fjgaude on 2007-10-25
The only thought coming to me is you might have assembled the array instead of creating it. Try to assemble.

```
sudo mdadm --assemble --scan --verbose
```

That might do what you wish.

---

### Post by carpespasm on 2007-10-25
is there anything i need to do to disasemble the old raid before this one or should i just assign it to something like md1?

---

### Post by fjgaude on 2007-10-25
Look, mdadm will find the old array, assemble it, and it will leave the name as it was. I turst it hasn't been wasted by some commands. Let mdadm decide what the name will be.

---

### Post by carpespasm on 2007-10-25
The reason i was asking was because when i ran the command you suggested it came up still reporting the following

```
storage@Storage:~$ sudo mdadm --assemble --scan --verbose
[sudo] password for storage:
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/disk/by-uuid/9caa1a88-1e66-488d-bd42-300d4b996dae: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: cannot open device /dev/hda5: Device or resource busy
mdadm: no recogniseable superblock on /dev/hda2
mdadm: cannot open device /dev/hda1: Device or resource busy
mdadm: cannot open device /dev/hda: Device or resource busy
mdadm: No arrays found in config file or automatically

```

I though that since the drives had been assigned to md0 that even though they're not mounted they could be held attached to md0 until i release them somehow. Thanks for the ideas, I'm trying to find anything I can on this, but I don't think I'm familiar enough with the commands to put it all together yet.

---

### Post by fjgaude on 2007-10-25
The only thing I can suggest is to study the man pages.

One way to release devices from an arry is the --stop command and also the manage mode:

```
sudo mdadm /dev/md0 -f /dev/sd[a][n]

sudo mdadm --stop --scan
```

The first removes any drive from an array; the second, stops any array that might be running.

Try to understand the manage mode... there might be something there that will save you.

---

