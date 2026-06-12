---
title: "Uninstalling ubuntu"
date: 2008-01-25
forum: General Help
---

### Post by Mr.popo on 2008-01-25
I still need help uninstalling ubuntu. I am running a dual boot with ubuntu and vista. How can I uninstall ubuntu leaving vista fine.
Please could you give me instructions.


Thanks

---

### Post by ugm6hr on 2008-01-25
I would recommend you install EasyBCD **first** (from within Vista):
[http://ubuntuforums.org/showpost.php?p=2668386&postcount=14](http://ubuntuforums.org/showpost.php?p=2668386&postcount=14)

Then you can just delete the Ubuntu partition (easiest from Ubuntu LiveCD Partition Editor).

Sorry to see you leaving...

---

### Post by Mr.popo on 2008-01-25
I may come back, Ill be active in the programming section.
I want to try fedora 8.


thankyou for the link mate.

---

### Post by Mr.popo on 2008-01-25
sorry for double post (Cant edit because of firefox problems in ubuntu- doesnt show button)

How would I delete the partition using the live cd?

Thanks,
Mr.popo

---

### Post by ugm6hr on 2008-01-25
> **Mr.popo said:**
> How would I delete the partition using the live cd?


If you want to install Fedora, you shouldn't need to delete the partition.  I haven't used the Fedora installer, but it should install on top of Ubuntu.

If you want to create "empty space" for Fedora to install in (assuming it has a Guided - use largest continuous free space installation option a la Ubuntu), then feel free to delete the partition as follows:
Boot LiveCD (Ubuntu)
Go to System-> Administration-> Partition Editor
Right-click on Ubuntu partition (make sure you get the right one - you don't want to wipe Vista! - it will probably be an ext3 partition) and select unmount (unless already unmounted), then select delete partition.
Do the same for the swap partition.
Then click Apply.
Then Shut down.

It's then gone, ready for a new partition to be created for Fedora.

PS: No offence, but if you are struggling with this, then programming may prove a bit tricky for you.

---

### Post by Mr.popo on 2008-01-25
Thanks,

Ive only really just switched to linux so im not that good with it.

---

### Post by rosegarden78 on 2008-01-25
Don't give up!  Try my post here:
[http://ubuntuforums.org/showthread.php?t=677959](http://ubuntuforums.org/showthread.php?t=677959)
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

I can't think of any reason why not to use Ubuntu.
Ok except CS3 and super industry media software.
And ABC website still OS-sniffs and blocks Linux.

---

### Post by rosegarden78 on 2008-01-25
Don't give up!  Try my post here:
[http://ubuntuforums.org/showthread.php?t=677959](http://ubuntuforums.org/showthread.php?t=677959)
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

I can't think of any reason why not to use Ubuntu.
Ok except CS3 and super industry media software.
And ABC still OS-sniffs and blocks HD streaming.

---

### Post by campbuds on 2008-01-26
when uninstalling ubuntu can you give the hard drive space back to vista for use?

---

### Post by ugm6hr on 2008-01-26
> **campbuds said:**
> when uninstalling ubuntu can you give the hard drive space back to vista for use?

Yes.  Just use the Vista partitioner afterwards to expand the Vista partition.  Or format as NTFS as a separate data partition.

---

### Post by Computer Guru on 2008-01-27
If you're planning on dual-booting Fedora and Vista, here's a guide that you may find useful:
[http://neosmart.net/wiki/display/EBCD/Fedora](http://neosmart.net/wiki/display/EBCD/Fedora)

---

