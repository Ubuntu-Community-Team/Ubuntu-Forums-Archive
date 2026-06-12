---
title: "[SOLVED] I deleted a partison and now I can't start Linux"
date: 2008-02-12
forum: General Help
---

### Post by NovaAesa on 2008-02-12
Hi all,

Today I was trying to delete one of my partitions because it was just sitting there as free space. I went into gedit and deleted that particular partition, thinking that later I could join the newly freed space with my /home partition. I realized that I would have to unmount /home to do this however, which I didn't really want to do at the time.

I had forgotten about it until I just restarted my computer (my wireless was playing up) but when I went to restart it, it didn't work. :( Here is a screen shot of what happened:
/
[[IMG]http://img87.imageshack.us/img87/817/dscf3470we0.th.jpg[/IMG]](http://img87.imageshack.us/my.php?image=dscf3470we0.jpg)

I know that all is not lost, because I am able to access my hard drive on the liveCD (which I am using now). Here is the contents of /media/disk-1/var/log/fsck/checkfs which is referred to in the screen shot:

```

Log of fsck -C -R -A -a 
Wed Feb 13 00:38:37 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sda4: clean, 18160/13910016 files, 22212319/27800482 blocks
fsck.ext3: Unable to resolve 'UUID=614296db-48bc-4fec-b2cf-d8a9e3d4986a'

fsck died with exit status 8

Wed Feb 13 00:38:37 2008
----------------
```


I really need to get this working again without loss of data, because I can't use my DVD drive to back anything up because the Live CD is in there.

If anyone could help me out with this, I would be ultimately grateful.

---

### Post by LaRoza on 2008-02-12
Use a live disk, and open:

/etc/fstab

(That is relative to the installation of Ubuntu, it will likely be in /media/sda1/etc/fstab)


Find the line that has this in it:
```

UUID=614296db-48bc-4fec-b2cf-d8a9e3d4986a

```
and comment it out (with a #)

It will most likely have this above it:

```

#/dev/sda4

```

How did you use gedit to delete a partition? I don't understand what you did.

---

### Post by NovaAesa on 2008-02-12
Okay, I commented out the line.
It had #/dev/sda3 above it though. I did it anyway.

Oh, I meant gparted before. It's almost 3am here, that probably has something to do with  my little mistake there :P

I'll post back when I've restarted and tested it out.

---

### Post by NovaAesa on 2008-02-12
Thank you La Roza!! That got it working.

If you lived on the same continent as you I would be soo buying you a beer right now (if it wasn't 3 in the morning).

---

