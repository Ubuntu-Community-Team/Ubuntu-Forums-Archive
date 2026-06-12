---
title: "can't remove 2nd zip drive icon from computer"
date: 2007-01-17
forum: General Help
---

### Post by pmdubuc on 2007-01-17
I've been fooling around with instructions on how to get a zip drive working and I think I've suceeded.  The problem is that in the process I somehow got two Zip Drive icons in my 'computer' location in the file browser.  The one called 'Zip Drive' works.  The other called 'Zip Drive 1' is bogus but I can remove it.  Its annoying me and might be confusing to other users.  Anyone know how to get rid of the thing?

Thanks,](*,)

---

### Post by bodhi.zazen on 2007-01-17
Have you tried ```
gksudo nautilus computer:///
```

Now delete the bogus zip icon ...

Oh, zip drives are typically /dev/sdx**4**

That is they are numbered 4, threw me for quite some time :)

---

### Post by pmdubuc on 2007-01-18
> **bodhi.zazen said:**
> Have you tried ```
gksudo nautilus computer:///
```

Now delete the bogus zip icon ...

Oh, zip drives are typically /dev/sdx**4**

That is they are numbered 4, threw me for quite some time :)

Yep, I tried that.  I get this error:

Error "Operation not permitted" while deleting "computer://...5201.drive".

Any other ideas?  I think this zip drive is /dev/hdd4.

---

### Post by bodhi.zazen on 2007-01-18
How do you mount the zip drive ? 

Do you have an entry in fstab ?

Where do you mount it ?

comment out (add a # at the front) if you have a line in fstab

# /dev/hdd4 .........

**Unmount, eject your zip disk**

```
sudo rm -r /media/Zip*
```

Or what ever mount point you use for Zip

Put the zip drive back in, open computer 

HTH

---

### Post by pmdubuc on 2007-01-18
That did it.  Thanks!  I found an error in the fstab that was causing the problem.

---

### Post by bodhi.zazen on 2007-01-18
8)

---

