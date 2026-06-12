---
title: "ubuntu not loading after trying to run the boot scripts"
date: 2008-04-13
forum: General Help
---

### Post by jorik42 on 2008-04-13
hi all; got a question

so, i found an old computer that ive  been trying to restore (which i have..all hardware seems to function); now i want ubuntu on it.  the thing is, i cant get it to boot.  it will turn on, load all the way through the splash screen. then simply freeze when trying to run /etc/____ /rc.local. (i dont know what goes between /etc/ and /rc.local; it just boots into the text only mode now)  alternately, it will load, then i get something like the following:

usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864  failed
usplash: Setting mode 1024x768  failed
usplash: Using mode 800x600
kinit: trying to resume from /dev/disk/by-uuid/3e1da8a4-d476-4b99-b714-522cf1673785
kinit: No resume image, doing normal boot...

Ubuntu 7.10 <computer name> tty1

<username> login: 


so, any idea of whats going on here?  do you think that this might be because i installed ubuntu on the HD while it was inside another box?  i was testing the HD and decided to just install ubuntu while it was in that computer; now im trying to put the HD in the computer its supposed to be in and i get the above error.  so, any thoughts?

---

### Post by starcannon on 2008-04-13
does the machine lack a CD drive?

What are the system specs for this machine?

If its truely old, say PII or K6-II/III old then I'd recommend Xubuntu, if its just got some stubborn hardware I'd recommend Alternate Install CD.

---

### Post by danwood76 on 2008-04-13
It is probably trying to load incorrect graphics drivers or some other hardware is giving issues.

What you should do is re install it on that machine, that way the configuration of the system will be correct for your hardware.

---

### Post by jorik42 on 2008-04-13
thank you all for your prompt replies.

the machine does have a cd/dvd drive in it; perhaps the dvd drive is too new and ought to be replaced with a straight cd drive?

as for the system specs, i have no idea; like i said i found it.   i can tell you its has 512 MB ram, and teh current HD is 120 GB.  i dont know the processor speed, however.  but it is an intel celeron of some kind.  

also, i cant get it read a live cd; ive tried my ubuntu install cd, as well as a gpatred live cd i have.  neither will boot; i suspect that this is because the boot priority is set to boot the HD first.  however, the system give me no BIOS to access, so im not sure how to change that.    or, at least its not showing a bios.

---

### Post by danwood76 on 2008-04-13
It must have a BIOS, when you hit the power button to turn it on just hit the 'Delete' button repeatedly, normally its the delete key, if this doesnt work it could be F2, F10 or F12.
With a bit of luck the bios config should pop up.

---

### Post by starcannon on 2008-04-13
Many computers will also give you a boot priority menu if you press esc at post.

And as the previous poster recommended, try the usual F keys F2 being most common, some machines also use Del key to get into bios.

---

### Post by jorik42 on 2008-04-13
yeah; i found it, and re-installed ubuntu.  everything works great now!  thanks alot!

jorik

---

