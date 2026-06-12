---
title: "bash: message output of blkid into a simple vertical list of partitions"
date: 2014-02-28
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-02-28
After about 20 hours of searching and trying this and that with sed and awk and for loops and whatnot, I'm at wit's end.  In a bash script is there any way to turn the output of blkid into a simple list consisting of just that portion of each line consisting only of the part appearing between "/dev/" and ":", each on a single line, like this:

hda1
sda1
sda2
sda5


No matter what I do with "delims=this" or "IFS=that" and no matter what I
pipe it to, the best I can seem to do is to get the first device only. Any way I manage to edit it at all, all the lines of the output of blkid are treated as one big line only, so that everything after the first ":" is thrown away.

As to why I want to use blkid instead of any of half a dozen other ways of starting, gives me almost exactly what I want: all partitions in the table, including the logical ones, and (I think) the unformatted ones, but not extended partitions and not unallocated areas. Ideally, it would leave out
the partition the system is booted from as well, but I have a routine that can remove that.

Thanks for reading.

---

### Post by steeldriver on 2014-02-28
```

$ sudo blkid -o device | sed 's:/dev/::'
sda1
sda5
sda6
sda7

```

```

$ while read -r b; do echo "${b/\/dev\//}"; done < <(sudo blkid -o device)
sda1
sda5
sda6
sda7

```

---

### Post by Dreamer Fithp Apprentice on 2014-02-28
Thanks, Steeldriver! Perfect!

---

