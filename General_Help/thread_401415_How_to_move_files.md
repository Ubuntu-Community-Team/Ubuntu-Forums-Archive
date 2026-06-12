---
title: "How to move files?"
date: 2007-04-04
forum: General Help
---

### Post by sandos on 2007-04-04
I tried moving my c:\wubi to d:, but I am not even allowed to open the files? I am administrator. I am on MCE of XP, and I cant seem to edit the ownership/permission of the files so I am unable to copy the files. :(

The thing is that grub doesn't work on C: for me. I am on a vgn-fe21m Vaio laptop with a SATA disk and getting error 17, c:\wubi\linux not found. I suspect this is a problem with the SATA chipset most likely? Seems to be a Intel 82801GBM/GHM (ICH7-M Family) controller. Any idea if this will work at all?

---

### Post by lcg on 2007-04-04
> **sandos said:**
> I tried moving my c:\wubi to d:, but I am not even allowed to open the files? I am administrator. I am on MCE of XP, and I cant seem to edit the ownership/permission of the files so I am unable to copy the files. :(
Since both C: and D: are Windows drive letters and you explicitly state that you are using MCE, how exactly is this problem related to Ubuntu?

> **sandos said:**
> The thing is that grub doesn't work on C: for me. I am on a vgn-fe21m Vaio laptop with a SATA disk and getting error 17, c:\wubi\linux not found. I suspect this is a problem with the SATA chipset most likely? Seems to be a Intel 82801GBM/GHM (ICH7-M Family) controller. Any idea if this will work at all?
And what has GRUB to do with your problem moving files??? I am afraid you will have to give us some more information before anybody can even try to give a helpful answer.
However, I doubt your GRUB problem (whatever it may be, your post isn't that detailed) comes from your chipset. I have Ubuntu installed on a Lenovo notebook with an ICH-7M and a S-ATA HDD and it works flawlessly.

Regards,
Lars

---

### Post by sandos on 2007-04-05
> **lcg said:**
> Since both C: and D: are Windows drive letters and you explicitly state that you are using MCE, how exactly is this problem related to Ubuntu?


Maybe not Ubuntu, but Wubi? I read that is seems to set the permissions a bit weirdly...

I seem to have the solution though: 

> Note You must be logged on to the computer with an account that has administrative credentials. If you are running Microsoft Windows XP Home Edition, you must start the computer in safe mode, and then log on with an account that has Administrative rights to have access to the Security tab.

I will try starting Wubi/grub/ubuntu from my D: partition, if that does not work I will try to give a more detailed error-report. The moving files part was simply because it did not start on C:, I wanted to try on D: since in another post that helped for someone. What sort of infomation do you want if it does not boot? It does not create any logfiles, understandably.

---

### Post by ago on 2007-04-05
> **sandos said:**
> Maybe not Ubuntu, but Wubi? I read that is seems to set the permissions a bit weirdly...
That will be changed in coming versions.

> What sort of infomation do you want if it does not boot? It does not create any logfiles, understandably.

It does, but if the errors are at the very beginning (grub) there is no time to activate the logger. If errors happen after the windows folder has been mounted, you should find the logs under C:\wubi\logs (in windows). Otherwise they are normally under /tmp (in linux).

---

### Post by sandos on 2007-04-05
For some reason, D:\wubi works fine, but C:\wubi does not. I wonder why this is? What are the common cause for error 17? I would like to know why it fails, not that it matters much to me but would be nice to help squash this "bug", if it is one.

Now the linux part of the install fails, it ends up on a red screen printing angry stuff. Can't remember the message I am afraid but I got a dialog about some failure.


[http://paste.ubuntu-nl.org/14004/](http://paste.ubuntu-nl.org/14004/)
[http://paste.ubuntu-nl.org/14005/](http://paste.ubuntu-nl.org/14005/)

---

### Post by sandos on 2007-04-05
Actually, rebooting into ubuntu again actually starts X without problems. Impressive. Now I need to see if anything is broken ;)

---

### Post by nothingspecial on 2011-09-26
Drift back to the wastelands of sleep.

Closed

---

