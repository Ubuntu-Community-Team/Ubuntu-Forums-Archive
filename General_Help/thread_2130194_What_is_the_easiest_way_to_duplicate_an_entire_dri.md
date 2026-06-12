---
title: "What is the easiest way to duplicate an entire drive"
date: 2013-03-28
forum: General Help
---

### Post by Victor43 on 2013-03-28
I have read that dd can do this for you but I need to download a 500MB live CD just to run this software. Is there any small size linux kernel bootable CD which comes with just dd that I can run in order to clone a hard drive. I use mostly Windows Vista and have not used Ubuntu in a long time.

Any suggestions would be appreciated.

Victor

---

### Post by Mark Phelps on 2013-03-28
Clonezilla is exactly what you need.  You should go to their website, download the ISO file and burn a CD of that.

Then, when you boot from that CD, you will the option to clone from one drive to another -- just realize the target drive has to be as large, or larger than, the drive you're duplicating.

---

### Post by jim_deadlock on 2013-03-28
What I've been wondering for a while is whether it's the size of the data, the partition or the physical drive that has to fit? If it's the partition, can you shrink the partition size to fit onto the target drive?

---

### Post by rnerwein on 2013-03-28
> **Victor43 said:**
> I have read that dd can do this for you but I need to download a 500MB live CD just to run this software. Is there any small size linux kernel bootable CD which comes with just dd that I can run in order to clone a hard drive. I use mostly Windows Vista and have not used Ubuntu in a long time.

Any suggestions would be appreciated.

Victor
hi
i use unix/linux since a long time - but never see a version wasn't coming without "dd". must be in /usr/bin
ciao

---

### Post by Victor43 on 2013-03-28
> **Mark Phelps said:**
> Clonezilla is exactly what you need.  You should go to their website, download the ISO file and burn a CD of that.

Then, when you boot from that CD, you will the option to clone from one drive to another -- just realize the target drive has to be as large, or larger than, the drive you're duplicating.

Thanks for the reply. Does CloneZilla do a sector by sector (byte by byte) of the entire drive ? I want everything copied from sector 0 of the source drive to sector N. Sort of like what a forensic would want when they duplicate a drive. 

Victor

---

### Post by kurt18947 on 2013-03-29
Here is another disk cloning tool.  I've not used it, just bookmarked it because it looked interesting.  I don't know if Clonezilla comes with the additional tools or not.

[http://redobackup.org/](http://redobackup.org/)

---

### Post by Mark Phelps on 2013-03-29
> **Victor43 said:**
> Thanks for the reply. Does CloneZilla do a sector by sector (byte by byte) of the entire drive ? I want everything copied from sector 0 of the source drive to sector N. Sort of like what a forensic would want when they duplicate a drive. 

Victor

Clonezilla has a drive cloning option -- and in that case, you can't shrink the partitions on the original drive as part of the cloning.  Even when copying partitions, Clonezilla still does not provide the option of shrinking the partitions on the original drive.

---

### Post by VanillaMozilla on 2013-03-29
You want a small Linux disc?  That's a no-brainer.  Get DSL.  And you can be sure it will have dd.  There's also a well-known rescue disc with all kinds of disc utilities, but it won't be as small as DSL.  I forget the name--maybe based on Knoppix.

---

### Post by Victor43 on 2013-03-29
@VanillaMoziThanks for the reply. I'll give DSL a try. [ 						 					]("http://ubuntuforums.org/member.php?u=311399") 				 				 					 						 	[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=311399")
@Mark thanks for the information on CloneZilla. However I've just read that CloneZilla will do a sector by sector cloning if the file system is of an unknown type. Will it still do a entire drive sector by sector if the file system (NTFS or FAT) is of a known type ?

---

