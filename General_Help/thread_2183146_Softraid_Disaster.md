---
title: "Softraid Disaster"
date: 2013-10-23
forum: General Help
---

### Post by Leldoren on 2013-10-23
[COLOR=#000000][FONT=Arial]Hello all, and thank you for your time.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have a softraid 5 array with 4 250GB hard drives. The drives were added to the array using the whole disk, no partitions, which I now know was the wrong way to do it. After a recent reboot it seems that an fsck was scheduled which ‘repaired’ two of the drives in the array. Running mdadm -E on the drives showed two of them being members of the raid5 array while the other two were now members of a raid0 array. After searching online I assumed that the mbr on the disks was corrupted. Fdisk reported that the drives were GPT, so I switched to gdisk which reported:[/FONT][/COLOR]


```
[COLOR=#000000][FONT=Arial]Problem: The CRC for the main partition table is invalid. This table may be[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]corrupt. Consider loading the backup partition table ('c' on the recovery &[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]transformation menu). This report may be a false alarm if you've already[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]corrected other problems.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Identified 1 problems![/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]After loading the backup table and no improvement I tried something else I found online:[/FONT][/COLOR]


```
[COLOR=#000000][FONT=Arial]mdadm --create /dev/md1 -l 5 -n 4 etc..[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]The new array was created and an hour later was synced. Now there is no filesystem.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]I know this isn’t much to go on, but I didn’t log anything, am I screwed here?[/FONT][/COLOR]

---

### Post by SaturnusDJ on 2013-10-24
I can't help on MBR/GPT and filesystem problems, but I can help with mdadm RAID.

You did a re-create but it looks like you forgot the most important part: the --assume-clean flag. This prevents a resync so existing data is untouched. A re-create is used to create the superblock again (as it was originally) with exact the same parameters as before (and as said: not sync data).

Now that data has been synced, you can safely assume everything indeed is lost.

---

### Post by Leldoren on 2013-10-24
Thanks for the response. Head down in shame... My wife is going to be sooo pissed.:-&

---

