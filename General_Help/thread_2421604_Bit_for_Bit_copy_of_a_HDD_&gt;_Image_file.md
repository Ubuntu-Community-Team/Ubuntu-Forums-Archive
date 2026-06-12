---
title: "Bit for Bit copy of a HDD &gt; Image file"
date: 2019-06-24
forum: General Help
---

### Post by amtrakuk on 2019-06-24
Hi there.

I have an old PVR with uses an internal 250GB 3.5" IDE disk is uses for storage.  As you appreciate the disk is getting old and closer to failure point.  Unfortunately I can't just replace the disk as the disk needs, the what appears to be some sort of bootstrap, if its not there as part of the startup test the PVR will flag the disk as faulty and wont go any further.  Getting hold of the service tools to prepare the disk as per the manufacture is nigh on impossible, partly due to the age and propriety code.

What I am thinking, IF the disk can be recorgnised in /dev/hda can I use a tool like 'dd' the disk to a 250 GB image file?  If so will that be an exact copy (including partition information, bootstraps not necessarily visible areas of the disk), if so what flags will I need?

Thanks in advance

---

### Post by TheFu on 2019-06-24
I would use ddrescue.  It keeps working when dd stops at the first failure.
All the options are spelled out in the manpage for each command. It is best to check the manpage ON YOUR SYSTEM for the option, since they change slightly over time and a web search might find the wrong options because your system has a different version of the tool.

```
sudo ddrescue {source} {target} {logfile}
```
so, if you plug in likely answers, then ... 
```
sudo ddrescue /dev/hdZ /opt/backup/disk.img /tmp/ddlog
```
Then swap the source/target to push the bits onto the new HDD.  The "Z" needs to be the actual disk for your system. dmesg should show it.

There are other tools that might work with compression like clonezilla or partimage or fsarchiver.  fsarchiver would be the most efficient, but I'm not 100% that it would work with a DVR "blessed" HDD.  I used ddrescue long ago to swap out a 120G TiVo S2 disk to a 300G TiVo disk. As far as I know, it still works, though it has been unplugged since hidef video happened.   ;(

---

