---
title: "total size of all files on a partition, easy way to get this in bash script?"
date: 2013-11-15
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-11-15
I need to get the total size of all files on a partition into a bash script. It doesn't have to be a pure number and it doesn't have to be exact, merely accurate to the last significant digit shown. For instance, it could be a string like "2.1 giB", with the unit being appropriate to the size being reported. 

The best approach I've been able to come up with is to use something like ```
df --total -h /dev/sda1
```but that puts out a table 3 rows by six columns. I suppose I could figure out how to massage that output with some of the string processing commands like awk or sed. I confess I always contemplate useing those commands with a certain amount of dread but perhaps that means I need more practice.

Is there some easier way? A command that will spit out something closer to what I want without embedding it in a lot of stuff I don't?

---

### Post by TheFu on 2013-11-15
df -h /dev/part.... | cut -f ....

---

### Post by steeldriver on 2013-11-15
Don't dread awk - could be as simple as

```

$ df -h | awk '$1 ~ /sda6/ {print $3}'
12G

```

or (if you need to run it for variable block devices) you can pass parameters in like

```

$ blockdev="sda6"
$ df -h | awk -v blockdev="$blockdev" '$1 ~ blockdev {print $3}'
12G

```

---

### Post by SeijiSensei on 2013-11-15
If you are willing to mount the partition temporarily, say to /mnt, you can use du like this
```
sudo du -s /mnt/*
```

You'll get a list of directories on the partition along with total size of the files in each directory.

---

### Post by Dreamer Fithp Apprentice on 2013-11-16
Thank you much, Gents!

Steeldriver's awk approach solves the immediate problem nicely, but I'll study all of these.

---

