---
title: "Total crash when using all ram"
date: 2007-10-30
forum: General Help
---

### Post by jcrnan on 2007-10-30
I think I might have messed up the buffering of my laptop. I tried out changing buffering to 0 to improve performance, but I didn't notice much difference so i set it back to 60.

But now it doesnt seem to buffer at all. And when I have lots of programs up and it uses 100% of the ram for applications (not including cache) it freeze completely. Nothing but a hard reset gets it back working. Any idea what the problem is?

I'm using Gutsy Gibbon

---

### Post by misfitpierce on 2007-10-30
You have a swap partition setup as well?

---

### Post by kerry_s on 2007-10-30
> **jcrnan said:**
> I think I might have messed up the buffering of my laptop. I tried out changing buffering to 0 to improve performance, but I didn't notice much difference so i set it back to 60.

But now it doesnt seem to buffer at all. And when I have lots of programs up and it uses 100% of the ram for applications (not including cache) it freeze completely. Nothing but a hard reset gets it back working. Any idea what the problem is?

I'm using Gutsy Gibbon

bufferring? do you mean swappiness?(vm.swappiness=1)
is your swap on?(swapon -a)
how much ram?

---

### Post by jcrnan on 2007-10-30
I have a 3Gb swap partition. And yeah, I mean swappiness, not buffering. I tried setting vm.swappiness=1, but now have it set to vm.swappiness=60

this is what I get if i "swapon -a"

swapon: cannot canonicalize /dev/disk/by-uuid/ddedabad-49a4-415e-9957-ee24ddc7ada3: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/ddedabad-49a4-415e-9957-ee24ddc7ada3: No such file or directory

---

### Post by forestpixie on 2007-10-30
can you post, or check  the output for these two - make sure the swap UUID is the same for swap in both cases

```
blkid
```

```
cat /etc/fstab
```

---

### Post by gromo3eka on 2007-11-01
> **forestpixie said:**
> can you post, or check  the output for these two - make sure the swap UUID is the same for swap in both cases

```
blkid
```

```
cat /etc/fstab
```

was helpfull for me. Thanks!

---

### Post by sot3 on 2007-11-04
Helpful for me, too - but does anyone know how an incorrect UUID got into fstab?

I used to have /dev/sda and /dev/sdb in there, and it appears that they were changed into UUID's when I upgraded to gutsy.  I've been struggling with low memory problems since then, and only today did I discover that a 'free -m' command revealed that I had no swap space allocated.

Thanks - you may have just saved me a few bucks.  But I'm thinking this is something the developers (and other people who have upgraded) would want to know about.

---

### Post by sot3 on 2007-11-04
Oh, one other thing - anyone know why my SATA disks no longer appear in df anymore, or more importantly how to get them there?  I'm guessing this is also related to the use of UUID's in fstab.

---

### Post by b5baxter on 2007-11-10
Helpfull for me too.

Another system with the wrong UUID in fstab.  What's up with that?

---

