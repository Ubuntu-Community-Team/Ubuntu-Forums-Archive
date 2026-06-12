---
title: "Painless return back to 32 bit"
date: 2007-05-16
forum: General Help
---

### Post by JuliusC on 2007-05-16
Anybody know if there are any painless way to return back my Ubuntu Feisty x86_64 to 32 bit one?

At home, I was working OK with Dapper till this week, when I update to Feisty using the 
'update-manager -c' to Edgy and later to Feisty but the results were not the same than at work where I did the same update, but from i686, in a similar box (basically AMD Athlon 3500).

Both are AMD Athlon 3500, 2Gb RAM, nVidia GeForce 6600. PC at work is a Shuttle xPC and at home one have similar hardware but was mounted by parts.
I don't want spent more time tuning my 64 bit box... then I prefer maintain both (work and home boxes) with the same Feisty (the 32 bit one) in order to have similar environments. In this way, if I change anything at work I will can do _exactly the same_ at home without worrying if it is full 64bit-compatible (vmware, anjuta, glade, acroread, flash, multimedia, etc ...)

Can I do a dist-upgrade after change the repos? 
Is it enough?

Thanks
--
JuliusC

---

### Post by kidders on 2007-05-17
> **JuliusC said:**
> Can I do a dist-upgrade after change the repos?No. A complete reinstallation is the most painless (ie the only practical) way to change the bitness of your OS.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by viciouslime on 2007-05-17
If you have a separate home partition (strongly recommended) then this will take you all of 15mins to stick a 32bit disc in and press next next next, let it work its magic and when you restart everything will be exactly as it was (except any applications you installed).

The only exception I have found to this is evolution, if you let 64bit evolution open your inbox and download mail you will get some errors the first time, however after pressing ok a few times, it will just work. Going the other way however, you loose any mail that was downloaded by 64bit evolution, you get the same errors but after pressing ok to them all the last mail in your inbox will be the last mail you received with 32bit evolution... must be something to do with the way it writes to the mbox file

---

### Post by kidders on 2007-05-17
> **viciouslime said:**
> must be something to do with the way it writes to the mbox fileYeah :-( This is quite true. Particularly when reducing your bitness, you should probably consider 32bit & 64bit Ubuntu to be about as intercompatible as Vista and OSX. Only the application preferences that fail to take full advantage of your 64bit CPU will survive the transition, I'd say.

---

### Post by JuliusC on 2007-05-18
Thanks, I'll do a Feisty reinstallation, I have separate root,  /home, /boot and data partitions for our three users.
I hope that applications settings were not very impacted. Later will come the applications re-install... :(

---

