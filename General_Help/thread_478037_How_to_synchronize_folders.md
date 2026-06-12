---
title: "How to synchronize folders?"
date: 2007-06-18
forum: General Help
---

### Post by bsalt on 2007-06-18
Hey guys, I'm looking for the best and easiest way to synchronize folder pairs similar to the SyncToy in Windows XP. I'm cool with using a command in the terminal if that is what it boils down to, but I'd prefer some way of synchronizing a folder on my local hard drive to a removable hard drive or a remote drive or something similar by the push of a button. Any ideas?

---

### Post by fdrake on 2007-06-18
good question, i would like to know that too. i found this for now [http://www.die.net/doc/linux/man/man2/fsync.2.html](http://www.die.net/doc/linux/man/man2/fsync.2.html) its a file sync command

---

### Post by Azakus on 2007-06-19
Are you thinking of rsync? rsync synchronizes data between multiple sources based upon the parameters given. Read the man page to learn more about it.
```
man rsync
```

---

### Post by Soarer on 2007-06-19
Yes - rsync will do the job for sure.

And there is grsync in the repositories if you want/need a GUI for it.

---

### Post by fragos on 2007-06-19
Rsync is a Linux favorite but you might find unison simpler to use.  I've used it to sink to a memory stick on both an Ubuntu and a Windows 2000 system.

---

### Post by bsalt on 2007-06-21
well i installed grsync and it works great, soarer

---

### Post by Soarer on 2007-06-22
That's great bsalt. Thanks for letting us know.

When you get confident, have a look (in a terminal) at "man rsync". It is pretty comprehensive, but needs to be read a few times before it becomes clear. rsync has lots of options you don't get with grsync, though if it works, don't fix it. :)

---

### Post by bill.blankenship on 2007-12-14
Fragos, thanks for the tip on unison. I did some reading and comparing between rsync and unison. I found a good article under Hack #86 in "Ubuntu Hacks" (O'Reilly, ISBN 0-596-52720-9). While rsync has some awesome capabilities, it looks like it only syncs in one direction. Unison, on the other hand, will do bi-directional synchronization. 

For those interested, Micah Carrick posted some instructions on setting up unison that are pretty easy to follow at the following URL:

[[COLOR="Blue"]http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html[/COLOR]]("http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html")

However, I found it far easier to simply use "Add/Remove..." to install the Unison GUI on the laptop. :)

Happy Hacking!

---

### Post by HermanAB on 2007-12-14
If you do bi-di synchs, make damn sure the clocks are right...

---

### Post by fragos on 2007-12-14
Good adivice on the time syncing.  As a single user with a desktop and a laptop that's not as much a factor but I still use NTP to sync my clocks.

---

### Post by geo909 on 2008-01-23
Hello and sorry for bringing this back to life, but I have a question after reading this:

> if you do bi-di synchs, make damn sure the clocks are right...

 When you say the "clocks" you mean ..er.. to synchronize the time?!

If this is the case, what's so special about being a minute or less inaccurate?!

---

### Post by fragos on 2008-01-23
ntp will keep your clocks correct and in sync.  If you're like me and syncronizing folders between my laptop and desktop it will make no difference because you aren't making changes to the same file at the same time on two machines.

---

### Post by geo909 on 2008-01-23
Yeah, I get it now..
*Real-time synchronization* you were talikng about..
Thanks!

---

