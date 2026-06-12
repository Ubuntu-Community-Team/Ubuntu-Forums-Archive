---
title: "Help concerning Linksys wusb54g version 2 and Ubuntu 7.10"
date: 2008-01-20
forum: General Help
---

### Post by dehnyen on 2008-01-20
I have been reading some how to's on getting this wireless adapter to work under Ubuntu 7.10 I know it's been posted here before, but I seem to still be at somewhat of a standstill. I'll give the short version:

I am running Ubuntu from the live CD right now, trying to get use to it before I wipe Windows XP. After researching for the past few hours, I have made a little progress, but am stuck again. I ran ndiswrapper version 1.51 from the terminal after putting the download in my home folder. That seemed to go just fine. I then changed to the ndiswrapper directory. The how to then said to run *make distclean.*That also seemed to go ok. Then it said to run *make*. Again, everything seemed fine. I ran into trouble when I ran *make install.* Everything seemed to be going along just fine until I ran into this error.

```
cannot remove '/lib/modules/2.6.22-14 generic/misc/ndiswrapper.ko' permission denied.
```

Note: I copied that to the best of my ability seeing as I forgot to throw the code on my thumb drive before exiting Linux.

I tried running *make* again and I was presented with a slew of errors. That was probably just a bone headed mistake from a new guy, heh. And finally, as Ubuntu was shutting down the system, it again presented me with several network shutdown errors that I have never gotten before when I rebooted.

My question is, what does that mean? Heh. I'm not exactly sure where to go. It seemed to create the ndiswrapper directory just fine. Everything was ok up until the end of the install it seems. What should I do?

One more question. As I said, I'm booting from the live cd. I do not have Ubuntu on my hard drive yet. When I get this wireless problem fixed, will everything transfer over once I decide to install to the hard drive or will I have to do all of this again?

Thanks for the help.

---

### Post by dehnyen on 2008-01-20
Selfish bump.

---

### Post by jleaker01z on 2008-01-20
When you issue the 'make install' command it need root priviliges.  Anytime something tells you to 'make install' add 'sudo' before it...so it reads 'sudo make install'.

That said, there is a ndiswrapper installation tool under Applications>Add/Remove .  Just open that up and search for 'ndiswrapper'.  Check the box next to it and click 'ok'.  Then ndiswrapper should be installed.

---

### Post by dehnyen on 2008-01-21
I think I did try sudo make install, but Im not positive. I've done so much work on things today it's all kind of turned to mush. I will try it again, thanks.

---

### Post by dehnyen on 2008-01-21
Update: Yes,  I went back into Ubuntu and redid everything using the sudo command before all of the installs. I'm still getting the same errors. Anyone have any ideas?

Thanks.

---

### Post by dehnyen on 2008-01-21
Last shot.

Anyone?

---

