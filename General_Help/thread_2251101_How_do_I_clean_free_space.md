---
title: "How do I clean free space?"
date: 2014-11-02
forum: General Help
---

### Post by bobmac on 2014-11-02
Folks,

 Not knowing the nuts and bolts of ubuntu:

Is there any way of cleaning the free space on a hard drive so that I can ensure that 'deleted' data (emails and so on) are actually removed from the disk.

Windows for example, has a 'cypher' command that overwrites the free space with random numbers.

Regards,

Bob

---

### Post by deadflowr on 2014-11-02
Look at the command shred
Run this in a terminal to get a quick overview
```
man shred
```

---

### Post by sudodus on 2014-11-02
If the files were already removed, and you want to wipe the remaining data from the disk surface, you can use zerofree.

```
 sudo apt-get install zerofree
```

```
 man zerofree
```

or do it 'manually' by writing zeros to a file until it has filled all free space (and then remove it). I think zerofree is more efficient, but I think it works only with ext file systems.

---

### Post by bobmac on 2014-11-02
sudodus,

Many thanks for the information. I've read the man entry for zerofree but I'm afraid it doesn't make much sense to me. I should have let you know in the first place that I'm in no way a techo type and don't understand much of what the 'man' stuff says.

It seems that I need to somehow make the filesystem read only. My problem is that I don't know how to do that.

I'd be greatful if you could assist me to sort all this out.

Regards,

Bob

---

### Post by sudodus on 2014-11-02
The best way is to boot from a DVD/USB drive (for example a live Ubuntu install system) and not mount (or unmount) the partition on the internal drive, that you want to treat with zerofree. (You cannot use zerofree on the filesystem of the running operating system.)

If Ubuntu is the only operating system, it is often installed in /dev/sda1. If installed alongside Windows (dual boot) it is often installed in /dev/sda5. You find that out with the following terminal window command (when you are still running the installed system from the internal drive).

```
df
```

Look for the device that is mounted on /

Check again with ***df*** after booting from the DVD/USB drive (the drive letter might have changed) and make sure which drive it is.

So ```
zerofree -v /dev/sdxy
```


where x is the drive letter and y is the partition number that you found with ***df***

-o-

But as usual, when doing something new and potentially risky, it is best to ***backup everything important before***.

---

### Post by bobmac on 2014-11-02
sudodus,

Fantastic many thanks for your patience for an old dodderer.

Regards,

Bob

---

### Post by sudodus on 2014-11-02
You are welcome and good luck :-)

---

