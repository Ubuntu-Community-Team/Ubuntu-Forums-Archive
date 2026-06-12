---
title: "Huge / size?!"
date: 2006-10-10
forum: General Help
---

### Post by lemonsCC on 2006-10-10
I just looked at my free space on my / partition and noticed I am using ~5.6gigs!  I know that the Ubuntu install is ~3gigs but could i have possible added 2.6gigs of plugins, apps, etc??  It isn't the contents of my home folder because that is on a different 10gig partition.

I also have a 8gig NTFS (windows 2000) partition and a 10gig FAT32 (shared) partition.

[IMG]http://img237.imageshack.us/img237/9151/screenshot1gc0.png[/IMG]

**Key**
hda1 - Windows Part.
hda5 - Shared Part.
hda6 - /home Part.
hda3 - / Part.

Thanks

---

### Post by nikhilk on 2006-10-10
One cause of this can be having several older kernel versions. You should keep one version older than the current kernel, as a fallback, in case something goes wrong. The others should be removed to reclaim disk space.

---

### Post by lemonsCC on 2006-10-10
well I found that 2.6gigs.  /usr and /var are 2gigs and 800ish gigs respectively.  Nothing in either of these folders is over 38megs

nikhilk: When I boot up GRUB only shows 2 kernels.

---

### Post by nikhilk on 2006-10-10
Yes, that is one more cause of "/" partition bloating up. Hence it is a good idea to mount "/usr" and "/var" on seperate partitions. You can quickly see where the space is being used the most.

---

### Post by epennings on 2006-10-10
You could try to delete the packages you dowloaded with synaptics/aptitude

```
sudo aptitude clean
```

edit : The system monitor is more accurate with used disk space. (See screenshot)

---

### Post by lemonsCC on 2006-10-10
I ran sudo aptitude clean and this is the disk space after that.  (Doesn't look much different.)
[IMG]http://img245.imageshack.us/img245/5512/screenshot1cl1.png[/IMG]

What could be taking up so much space in /usr and /var?  I remember having issues with huge log files on a previous install, but I don't see the enourmous files that I had before.

EDIT:  It looks like /var is a more reasonable size now, at 136MB.  There is also 400MB of openclipart in /usr.  This would bring the system size to 4.6GB is this reasonable, becuase epennings / partition is only 2.6GB?

---

