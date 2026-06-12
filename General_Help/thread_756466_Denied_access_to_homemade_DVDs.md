---
title: "Denied access to homemade DVDs"
date: 2008-04-15
forum: General Help
---

### Post by phil_bell on 2008-04-15
My Ubuntu computers mount video DVDs from my Panasonic DVD recorder as DVD-ROM, but deny me access to the files.  I can play the DVDs, but I can't open, read or copy the files.  However, my Ubuntu computers mount video DVDs I've authored with software as DVD-R or +R repectively, with full access to the files.

Thinking that there may be something strange with the Panasonic recorder disks, I tried them using my Debian and Windows partitions on the same computers. I was surprised to see that Debian and Windows mount the same video DVDs from my Panasonic DVD recorder with full access.  I can open, read and copy the files.

So the problem seems to be specifically with the way that Ubuntu mounts video DVDs from my Panasonic recorder.

Does anyone know what is going on here?  I have several work-a-rounds, but I would like Ubuntu to be able to mount the discs properly from the start.

---

### Post by gsmanners on 2008-04-16
You should probably note what differences in the "/etc/fstab" file between Ubuntu and Debian. Usually, the line for such a device would look like:

```
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Subtle differences in various options here might affect whether some discs mount properly.

---

### Post by phil_bell on 2008-04-19
Thank you for answering my post.  Well, I found a solution.  I opened the fstab files on both partitions.  The Debian mount options for the DVD drive are

     user,noauto

and the Ubuntu options are

     user,noauto,exec


First, I tried removing the 'exec' mount option in my Ubuntu fstab to make it like Debian, but I was still denied access to the files.  Then I put back 'exec' and added 'utf8' to make it look like your example.  Access denied.  Next, I tried 'uid=phil'.  Access denied.  And next, I tried adding 'norock' even though I didn't know anything about Rock Ridge extensions.  SUCCESS!  Just for fun I removed 'norock' and added 'nojoliet'.  SUCCESS AGAIN!  Now Ubuntu displays a DVD-R/+R icon, respectively, instead of a DVD-ROM icon when I mount the Panasonic discs and I have full access to the files.

Finally, I looked up Rock Ridge and Joilet extensions on Wikipedia to learn about what I was disabling (maybe I should have done that before experimenting).  I guess Debian Etch must have Rock Ridge and/or Joilet extensions disabled somehow other than in /etc/fstab.

---

