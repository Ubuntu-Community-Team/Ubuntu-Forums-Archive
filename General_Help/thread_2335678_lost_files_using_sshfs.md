---
title: "lost files using sshfs"
date: 2016-08-31
forum: General Help
---

### Post by jhodgo on 2016-08-31
Hi all,

I have had something of a major disaster. I had a Ubuntu (14 LTS) installation under which I had an sshfs folder set up to sync a bunch of files and directories. A few days ago, after trying to install some python modules, the Ubuntu installation completely died (with a "Kernel panic - not syncing exitcode=070007f00" error), which I have been unable to resurrect. So, I performed the nuclear option and formatted my second hard disk, installed Kubuntu (16 LTS) onto it and copied my old home directories across. 

This worked more-or-less fine, except that when I re-setup the sshfs, I found that a number of (quite important!) files had not synced with the server. Does anyone know how I could possibly retrieve the files that had not synced by ssh?

Cheers

---

### Post by HermanAB on 2016-08-31
So, you still have the previous hard disk?  If so, stick it into a USB disk enclosure, plug it in and see what is there.

---

### Post by SeijiSensei on 2016-08-31
If you don't have an enclosure, I've found devices like this work very well, too: [http://www.newegg.com/Product/Product.aspx?Item=N82E16812232002](http://www.newegg.com/Product/Product.aspx?Item=N82E16812232002)

---

### Post by jhodgo on 2016-08-31
> **HermanAB said:**
> So, you still have the previous hard disk?  If so, stick it into a USB disk enclosure, plug it in and see what is there.

I still have the previous hard disk, and it is still accessible, but if I try to access the directories it is empty. I figure that the files must have been stored *somewhere* and I doubt they were deleted, so hopefully it's just a matter of working out where?

Cheers

---

### Post by SeijiSensei on 2016-09-01
Does the drive have a "lost+found" directory?  Did you look there?

---

### Post by jhodgo on 2016-09-06
Yes, I looked in there too. I've even gone to the point of using photorec to recover the files, but so far with no success. If anyone knows "where" sshfs files are mounted, that would be really helpful.

Cheers

---

