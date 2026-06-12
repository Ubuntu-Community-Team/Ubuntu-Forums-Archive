---
title: "Drive failure and recovery advice"
date: 2007-08-07
forum: General Help
---

### Post by Finster101 on 2007-08-07
Today when booting my Ubuntu system I got a really bad series of messages like:

Buffer I/O Error on device hdb1, logical block 0
Buffer I/O Error on device hdb1, logical block 1
...

So since I've never experienced something like this and the system never seemed to boot I'm guessing the drive has failed.  This leads me to a number of questions:
   
Is there any thing I can do to try to recover the data?  

Is there a certain procedure I should follow?  

Any specific tools/distros that would help?

Should or could the drive be recovered as an image?  Should I purchase a new drive of the exact size?

Should I try to only recover my files or the entire OS?

Sorry for so many questions and thanks in advance.

---

### Post by phidia on 2007-08-07
Arguably the best idea may be to try a live cd. After you have sucessfully booted a live cd  e.g. ubuntu, [knoppix]("http://www.knoppix.com/"), [nimbleX]("http://www.nimblex.net/")....there are plenty out there. Some people here recommend [systemrescuecd]("http://www.sysresccd.org/Main_Page") you can then try and mount the partition(s) that are involved and if you can mount and read them you will be able to copy or burn your data to disc.

---

