---
title: "Selecting good filesystem for Virtual Machine"
date: 2013-10-14
forum: General Help
---

### Post by savagetwinky on 2013-10-14
I've been trying to gather some good info on performance from filesystems. We started doing linux development not to long ago at my company but our corperate is strictly windows. We also are stuck with incredibly intrusive virus scans + encryption. This causes quite a bit of pain using something like yocto, where I'll go to build something and my system essentially locks up for 6 hours while its building (... day off i guess)

So I'm trying to find the best filesystem choice for my environment. Its ok if it doesn't have journaling, I can use VMware's snap shotting for backups. 

I'm also curious if its better to split up the virtual disks for multiple files, they say it performs worse but I imagine one large file might cause more issues with the encryption + virus scan.

Any help would be much appreciated, i've had a hard time finding info on these types of issues. If you have any other suggestions like which desktop environment might be better for alleviating some of the issues that would also be good. Currently its kind of brutal working with Linux and the problem is windows ;(

---

