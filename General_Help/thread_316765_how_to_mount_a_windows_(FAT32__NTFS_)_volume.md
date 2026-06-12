---
title: "how to mount a windows (FAT32 / NTFS ) volume"
date: 2006-12-11
forum: General Help
---

### Post by dalebuk on 2006-12-11
](*,)  How do I mount a windows hard drive in Dapper LTS? ( full access )
 An easy and not to diffcuilt way, if possible.
I need to look at different windows hard drive on a regularly. 
So a simple method if they is one please.

---

### Post by taurus on 2006-12-11
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by etaham on 2006-12-11
look up ntfs-3g here in ubuntu forums. installing it and setting your hd's up with it will allow you read/WRITE access to ntfs drives

---

### Post by bulldog on 2006-12-11
> **etaham said:**
> look up ntfs-3g here in ubuntu forums. installing it and setting your hd's up with it will allow you read/WRITE access to ntfs drives

It should be good thing to tell it's not entirely safe to use and you can destroy your NTFS disk.
If you want to promote this,warning people is the least you can do.

---

### Post by rajeev1204 on 2006-12-11
hi
no offence to the forum staff but the easiest method to mount a FAT 32 partition is given in the system documentation itself


go to system/help/system documentation

select ubuntu desktop guide and check under partitions and booting

follow the simple instructions and voila

u r good to go !

iam not sure its safe for NTFS ( not recommended)

---

### Post by szaka on 2006-12-11
> **bulldog said:**
> It should be good thing to tell it's not entirely safe to use and you can destroy your NTFS disk.
Hi bulldog. The ntfs-3g development team would like to know how is this possible. Could you please elaborate the problem you had, or show an example how to destory NTFS, or point to somebody who had such experience with ntfs-3g, so we could contact him/her, investigate and fix this serious problem, if it's indeed in the ntfs-3g driver?

In the past we have tracked down already several hardware problems and Microsoft NTFS driver problem ([http://support.microsoft.com/kb/925308/](http://support.microsoft.com/kb/925308/)) which originally were believed to be caused by ntfs-3g. But we can never know, and ntfs-3g could also have a bug we are not aware of yet. 

We take NTFS integrity VERY seriously and never released any driver which we thought could destroy NTFS. I think our test suite is fairly extensive and several users/testers/developers keep trying to intentionally destory NTFS without success: [http://www.ntfs-3g.org/quality.html#testmethods](http://www.ntfs-3g.org/quality.html#testmethods)

Though, of course we could have missed something and your help would be greatly appreciated if you're aware of any NTFS destruction related problem in the latest ntfs-3g driver. Thank you a lot!

---

### Post by dmartinsca on 2006-12-11
> **bulldog said:**
> It should be good thing to tell it's not entirely safe to use and you can destroy your NTFS disk.
If you want to promote this,warning people is the least you can do.

Maybe you are thinking of the ntfs in-kernel drivers which provided partial write-support? Although from my experience with them, they were restricted so much that they couldn't really cause any harm either. Please try not to spread incorrect information:p

Although there is always a chance, with any filesystem driver that something can go wrong, you make it sound likely that you'll lose data, when in reality the ntfs-3g driver has been extensively tested & has proven reliable.

---

