---
title: "How can I maintain my drive order (sda, sdb, etc)"
date: 2021-06-26
forum: General Help
---

### Post by sofasurfer on 2021-06-26
My system operates on sda6 (an sata drive). I attached a secondary drive (an ata drive full of files) and then my system drive becomes sdb6 instead of sda6 and the secondary drive now takes its place as sda. How can I maintain my system drive as sda6 and the secondary drive as sdb?

---

### Post by TheFu on 2021-06-26
change the cables around, but sda / sdb are never guaranteed. That's why we use UUIDs and LABELs in our partition mount config files.

The last 20 yrs, UUIDs have been preferred. The sd? name doesn't matter. It used to be that each port had a specific name connected to it, but then enterprise users started connecting hundreds of HDDs to their systems and keeping track of more than 25 names became a problem.  

The UUID was the solution. The goal was to make each partition have a unique ID that wouldn't conflict on the same system. Don't read any more into it. The fact that they are impossible for humans to remember is a bonus. If you want something that a human can memorize, then set a LABEL on each partition and mount using that instead.  The LABEL= mount method is great for external USB storage devices. It will also make the automatic mount location make sense, as the LABEL is used for the directory name.  /media/{username}/{LABEL} is how those work.  There are all sorts of reasons NOT to allow that, but for a casual Linux user, it is easy.

---

### Post by oldfred on 2021-06-26
If I plug a flash drive in and it default to sdd, but reboot, flash drive becomes sda and every other drive changes.
Default mount by UEFI/BIOS is in SATA port order, but other drives may not follow that.
Put first drive in SATA0, second in SATA1.

---

### Post by sofasurfer on 2021-06-26
Thank you. My biggest gripe is that gparted, which I always run when messing with partitions so I have them properly identified, does not have UUIDs readily listed. I have to look in properties for each individual drive. I don't suppose gparted can be edited to show UUIDs in the graphic display?

---

### Post by sudodus on 2021-06-27
[FONT=Courier New]**lsblk**[/FONT] can be helpful. You can run something like the following examples in a wide terminal window (maybe fullscreeen to avoid truncating the lines of the output),

```

lsblk -f
# or
lsblk -o name,size,fstype,label,uuid,mountpoint,model

```

---

### Post by TheFu on 2021-06-27
**lsblk** with good options is pretty nice.  Just setup an alias or two to make it easy.  Needing the UUID happens so infrequently that I don't have any aliases for that.

There are other commands, like **blkid**, which can provide the information too, just not as nicely.

BTW, I use **gparted** too for partition management, if it is available. Alas, servers don't have a GUI, so gparted doesn't run on them. 

Learning to use the CLI interfaces is a useful skill for many people.

---

### Post by oldfred on 2021-06-27
If using gparted scroll to a partition, and right click, at bottom is information which shows UUID.
But gparted shows labels, and I try to remember to always label partitions.

---

