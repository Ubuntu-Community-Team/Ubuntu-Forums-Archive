---
title: "Migrating computers"
date: 2014-03-30
forum: General Help
---

### Post by Ertai87 on 2014-03-30
I have 13.10 installed on my laptop, but my laptop is kind of crappy so I'm buying a new one.  I'd like to put Ubuntu on it the easiest way possible.  Is it possible to simply remove the hard drive from my existing laptop and insert it into the new one, or do I have to do a full format and reinstall?

Thanks.

---

### Post by carl4926 on 2014-03-30
I'd recommend a clean install to benefit from everything the new machine has to offer. You can backup you user account and transfer that and all your settings.

FYI: It is possible that transferring the HDD would work though, that or doing a dd image from one to the other

---

### Post by Ertai87 on 2014-03-30
If I insert the old hd into the new computer and do a backup + reinstall, will that work?  That seems like a good compromise and won't take forever.

---

### Post by carl4926 on 2014-03-30
You loose the benefit of the new HDD that came with the new machine
I find, making a backup of my /home
And doing a clean install 
Doesn't take any longer in most cases

What is the difference between what you describe and 
Doing a backup and doing a clean install on the new hardware, then copying over your backed up files?

---

### Post by sudodus on 2014-03-30
> **Ertai87 said:**
> I have 13.10 installed on my laptop, but my laptop is kind of crappy so I'm buying a new one.  I'd like to put Ubuntu on it the easiest way possible.  Is it possible to simply remove the hard drive from my existing laptop and insert it into the new one, or do I have to do a full format and reinstall?

Thanks.

In general, ***yes***, but if you have proprietary drivers it may not work. Typically you might have proprietary drivers for graphics and wifi. If that is the case, you can remove them, and let the computer use the built-in free drivers, and your Ubuntu should be portable.

> **Ertai87 said:**
> If I insert the old hd into the new computer and do a backup + reinstall, will that work?  That seems like a good compromise and won't take forever.

I have made many portable systems, that can be ported either via

- ***dd*** (which is possible if there are no bad sectors on the drive) but slow and risky,

- *** Clonezilla*** (make a clone of the whole drive). If you make a  (compressed) image of the whole drive you have a good backup of the  complete system, that can be cloned into a drive of the same or larger  size,

- the ***One Button Installer***: make a tarball of your system  (works with BIOS systems but not with UEFI). The system can be installed  into a new drive from the tarball without the strict size limit of  Clonezilla, but of course, there must be space enough to expand all  files from the tarball.

But backup can mean many things, there are backup systems that only backup [some] files, not the complete system including boot-loader, partition table and all system files.

---

### Post by Ertai87 on 2014-03-30
@carl: If for whatever reason I decide to migrate back to Windows, I can save the Windows install on the other drive to save time later.

@sudodus: By "backup" I meant a reinstall with included migration of my current home folder.  Sorry if my reply was unclear.

---

### Post by sudodus on 2014-03-31
Fine, you know what you are doing :-)

---

### Post by Ertai87 on 2014-03-31
Bought the new computer, moved the HD over.  I think Ubuntu doesn't support the graphics stuff on the new machine.  I think this thread is over, but if you guys could go check out my new thread at [http://ubuntuforums.org/showthread.php?t=2214345](http://ubuntuforums.org/showthread.php?t=2214345) it would be appreciated.

---

