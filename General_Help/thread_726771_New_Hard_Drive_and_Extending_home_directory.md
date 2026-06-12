---
title: "New Hard Drive and Extending /home directory?"
date: 2008-03-17
forum: General Help
---

### Post by Midvale on 2008-03-17
Thanks to anyone taking the time to read this.

I've read through a few posts on how to move and back up my /home directory but what I really want to do is take me current /home folder on a 200 GB hard drive, and extend it on a new 160 GB hard drive that I've installed.   Is it possible to span your /home directory over hard drives without configuring raid or LVM?  And I was going to use a sym link but I'm not sure how that works exactly.  

Right now I have the new drive installed and partioned under / and it works, but I would rather have it as a /home folder and have my /home folder be 360 GBs if that makes sense.  Maybe I missed a How-To on how to do that but the ones I've read through consisted of backing up and copying data from one point to another.  

Any help or guidance wold be appreciated.

---

### Post by Oldsoldier2003 on 2008-03-17
> **Midvale said:**
> Thanks to anyone taking the time to read this.

I've read through a few posts on how to move and back up my /home directory but what I really want to do is take me current /home folder on a 200 GB hard drive, and extend it on a new 160 GB hard drive that I've installed.   Is it possible to span your /home directory over hard drives without configuring raid or LVM?  And I was going to use a sym link but I'm not sure how that works exactly.  

Right now I have the new drive installed and partioned under / and it works, but I would rather have it as a /home folder and have my /home folder be 360 GBs if that makes sense.  Maybe I missed a How-To on how to do that but the ones I've read through consisted of backing up and copying data from one point to another.  

Any help or guidance wold be appreciated.

its better just to create a data partition and link it to a folder in your home dir. raid wont do what you are proposing...

---

### Post by bigredradio on 2008-03-18
Yeah, I agree with the last post. If you really do not want to use LVM (dunno why not), then create different partitions on the other disk, create filesystems on those partitions and mount them in your home directory. /home/user/Movies /home/user/Pictures  - you get the idea.

---

