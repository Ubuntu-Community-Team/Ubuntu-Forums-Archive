---
title: "File syncing home network Ubuntu-W7"
date: 2013-03-20
forum: General Help
---

### Post by evilbrent on 2013-03-20
Hi,

I've googled every google I can, and I'm sure this is simple, but it's just beyond my grasp.

Can I sync folders on two computers in my house (Ubuntu 12.04 and Windows7) such that when there's a change on one file it automatically changes the corresponding file on the other computer?

I need a setup that will survive computer restarts, and work automatically in the background. Everything I find seems to need to be run manually, or runs as a program but not at startup. I thought I was close with Lucky, and Unison, but no cigar.

We've just gone from one family computer to two, and we're kind of going on a hot-seat basis, rather than a your-pc/my-linux basis: there's always someone sitting on the machine you want to use, it'd be good if it didn't matter what machine got used... So I need it to sync my wife's hobby-business stuff, and my son's minecraft stuff, and preferably automatically backup photos and documents etc.

Any suggestions? Is this something that rsync can do?

---

### Post by kuifje09 on 2013-03-20
While I cannot give you a perfect answer, I would suggest to read this ( I have no experiance with them )

[https://www.itefix.no/i2/cwrsync](https://www.itefix.no/i2/cwrsync) 

[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)

And search for such rsync alike tools for windows. 

With rsync you can update the filesystems on both sides.
Watch out when configuring to delete  the deleted files .. you can delete too soon too much....

There are at least 2 windows rsync tools for this job. You could even use cygwin, but I think it is overkill.

---

### Post by 2F4U on 2013-03-20
Why don't you use some kind of network harddisk or NAS (network attached storage)? Your data wouldn't reside on one particular computer, but would instead be stored on media that is accessible through your home network (only works if you actually have a network). No need to sync since the data is stored in one common place.

---

### Post by kurt18947 on 2013-03-20
> **2F4U said:**
> Why don't you use some kind of network harddisk or NAS (network attached storage)? Your data wouldn't reside on one particular computer, but would instead be stored on media that is accessible through your home network (only works if you actually have a network). No need to sync since the data is stored in one common place.

I was having the same thought and there are routers around that have a USB port.  That USB port can be either a printer server or it can support a USB storage device.  I don't have one but have done a bit of research.  Or as  suggested a NAS device which can plug into an ethernet port on your existing router.

---

### Post by kuifje09 on 2013-03-21
Very nice a NAS on you network, but a software solution would work as he asks for.
Secondly, a software solution is a lot cheaper if you already have the diskspace avaliable.
And If you dont have a NAS with a raid solution you are better of with a rsync solution.

---

