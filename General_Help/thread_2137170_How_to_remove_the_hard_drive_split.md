---
title: "How to remove the hard drive split?"
date: 2013-04-19
forum: General Help
---

### Post by xXPhasemanXx on 2013-04-19
When I was installing ubuntu it told me that I had to split my hard drive. I did, and now I uninstalled ubuntu, but the hard drive split is still in place. Is there any way to undo this?

---

### Post by tgalati4 on 2013-04-19
Boot a Live Ubuntu DVD and use gparted to delete the 2nd partition and expand the first partition to fill the space.

---

### Post by xXPhasemanXx on 2013-04-20
> **tgalati4 said:**
> Boot a Live Ubuntu DVD and use gparted to delete the 2nd partition and expand the first partition to fill the space.
So basically I go to install it again, but fill one of those hard drives splits into the entire space?

---

### Post by oldfred on 2013-04-20
No, from liveDVD or flash use gparted to delete the Linux partitions. And only if first partition is XP then you can use gparted to expand the XP partition.
If Vista or Windows 7 use disk tools in Windows then to expand Windows into the unallocated space.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by xXPhasemanXx on 2013-04-20
> **oldfred said:**
> No, from liveDVD or flash use gparted to delete the Linux partitions. And only if first partition is XP then you can use gparted to expand the XP partition.
**If Vista or Windows 7 use disk tools in Windows then to expand Windows into the unallocated space.**

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

I use Wndows 8, does that change anything?i

---

### Post by oldfred on 2013-04-20
Should be the same. Always best to use Windows to resize Windows NTFS partitions and it will then run chkdsk on reboot. But do not create new partitions with Windows as it may convert to dynamic partitions which does nto work with Linux and can cause issues in Windows.

And I think it would be the same if Windows was pre-installed and gpt partitions, just with gpt and UEFI booting Windows has a lot more partitions as part of a standard install.

---

### Post by HermanAB on 2013-04-20
Just bear in mind that when you mess around with partitions, then you can lose all your data.

---

### Post by xXPhasemanXx on 2013-05-01
Is there no way to do this without a chance of losing all my data?

---

### Post by |{urse on 2013-05-01
> **xXPhasemanXx said:**
> Is there no way to do this without a chance of losing all my data?

Yes, copy the drive to another drive using clonezilla or similar software. If the current hard drive has a booting OS then boot it up and burn your files to DVD or copy them to a flash drive. Data that does not exist in 2 places simply does not exist.

---

### Post by xXPhasemanXx on 2013-05-01
> **|{urse said:**
> Yes, copy the drive to another drive using clonezilla or similar software. If the current hard drive has a booting OS then boot it up and burn your files to DVD or copy them to a flash drive. Data that does not exist in 2 places simply does not exist.

Thanks for the help.

Is there any other way to undo the split? I'm having some trouble with this method.

---

### Post by |{urse on 2013-05-08
No, not really, you will have to use a partition manager like gparted.

---

### Post by xXPhasemanXx on 2013-05-08
> **|{urse said:**
> No, not really, you will have to use a partition manager like gparted.
Okay, thanks for the help. I'll try that out

---

