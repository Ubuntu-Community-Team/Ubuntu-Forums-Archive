---
title: "Dell 6400/E1505 questions"
date: 2006-08-28
forum: General Help
---

### Post by ecto on 2006-08-28
Hello, fellow ubuntu-ers its been a while since ive posted
In any case. I have started college and thought about getting a laptop for school.
The laptop I have decided on getting is the Dell Inspiron 6400 E1505 because I have read many accounts which ubuntu was successfully installed on it.
I have read several guides on how to install ubuntu on the 6400 and all of the accounts seem to be a painless install unlike other laptop makes. However on one HOWTO i read about Dell's special MBR. I read that you have to backup and restore MBR using certain tools. As i was reading the methods on how to backup and/or restore the MBR it says that I must have a copy of the "boot code" taken from a previous dell or otherwise. My main problems are that 
1) This is going to be my first Dell Laptop
2) I dont know where to get the Boot Code or how to obtain it
3) I still dont quite understand how I am suppose to save and restore the MBR code in the first place.
Has anyone installed ubuntu on a Dell Inspiron 6400/E1505 and dealt with the special MBR? Is backing up the MBR really necessary? Doesn't Dell give you a recovery disk that should already "restore" the MBR? 
Thanks for all your help in advance
--------------
n0dl

EDIT: By the way I was talking on #ubuntuforums where a friend told me that I need to delete any swap space i have because it causes debootstrap errors or the like. Im not sure why. Any other oddities I should keep in mind when in installing or a reason for needing to delete the swap space (i would think you need it so your computer wont thrash...)

---

### Post by eternalsword on 2006-08-29
AFAIK dell no longer gives out recovery discs unless the buyer purchases one.  I just bought a system over the summer and it didn't come with one.  Granted I didn't want one anyways since I already had an XP pro key and the system that came with it was Media Center Edition.  I believe the new MBR is not very useful, just a ploy to the uninformed.  Much better to reformat and install from scratch when such problems arise that would require it, granted the need to backup files becomes greater, but even system restore does't restore all files to a good state and factory restore from the hard disk is a pain in the neck waiting to happen.  So just make sure you purchase the recovery disc along with the system.

---

### Post by Daniel15 on 2006-09-08
> AFAIK dell no longer gives out recovery discs unless the buyer purchases one
The Dell Australia site didn't give me the option of getting a Recovery CD, so I'm assuming that it will come with one?

---

