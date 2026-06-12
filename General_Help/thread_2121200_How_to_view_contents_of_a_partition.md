---
title: "How to view contents of a partition?"
date: 2013-03-01
forum: General Help
---

### Post by nickdc on 2013-03-01
I feel like an "absolute beginner" again by asking this, but I've found nothing clear so far. I've just successfully moved my Home folder to a separate partition to allow more space for expansion and am about to do the same on my partner's pc, *where I cannot afford to screw up!* So before making any changes I want to actually look into her two main linux partitions, sda5 and sda6, to double-check they contain what I think they should. I can see from using Gparted what proportion of the partitions contain data, but not what that data is. I know how to list the contents of a directory using the terminal, but with the file system being directory based, I don't know the correct commands (if such exist - but presumably they do, given linux's flexibility) to list the entire contents of an individual partition. (And if there's a GUI method as well, so much the better.)

---

### Post by The Cog on 2013-03-01
Something like this perhaps?
```
sudo mkdir -p /mnt/a5
sudo mount /dev/sda5 /mnt/a5
sudo find /mnt/a5 | less
sudo umount /mnt/a5
```

---

### Post by nickdc on 2013-03-04
Thanks for coming to my assistance, The Cog. Sorry I've not acknowledged before now - other issues came up which had to take precedence. Your code worked, but I soon realised I shouldn't have said "entire contents"! I really only needed to check what folders/directories were there. Your code produced a mammouth screed which I didn't know how to control. I ended up having to kill the process and made a mental note to take some tutorials in using the terminal! :)

---

### Post by schragge on 2013-03-04
Well, then replace the 3rd line (*sudo find /mnt/a5 | less*) with *ls /mnt/a5*

But if all you need is to check whether any directories and/or files are present then you can do it even without mounting the filesystem in question:
```

grub-fstest /dev/sda5 ls /

```The output is similar to that of
```

sudo mount /dev/sda5 /mnt
ls -px /mnt
sudo umount /mnt

```

---

### Post by cortman on 2013-03-04
Replace

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo find /mnt/a5 | less
```

with

```
 sudo find /mnt/a5 -type -d
```[/FONT][/COLOR]

---

### Post by nickdc on 2013-03-04
Thanks schragge and cortman, that's really useful help. A little knowledge gained - many thanks.

---

