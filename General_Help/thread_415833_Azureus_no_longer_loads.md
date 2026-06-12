---
title: "Azureus no longer loads"
date: 2007-04-20
forum: General Help
---

### Post by b0ng0 on 2007-04-20
I have had trouble with Azureus in Ubuntu 7.04. I recently added a torrent and it crashed. Now evertime I load it, it loads at teh splash screen and the main window comes up then it just closes every time. I have uninstalled it, reinstalled but none of this seems to work. Can anyone help?

Thanks

---

### Post by taurus on 2007-04-20
Try to run it from a terminal to see what the problem is.

Applications -> Accessories -> Terminal
```
azureus
```

---

### Post by b0ng0 on 2007-04-20
It comes up with this:

# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=9934, tid=3085200272
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid9934.log

I think it was generally fine until I installed the java plugin for firefox but I can't be sure,.

---

### Post by Havoc on 2007-04-21
Same issue here. I installed azureus, then installed sun-java6-bin and plugin, worked with that, rebooted, and azureus won't load now. Same exact problem. I'll try downgrading to sun-java5-bin.

---

### Post by vishnumrao on 2007-04-21
Hi,

I have a similar problem with Azureus. [http://ubuntuforums.org/showthread.php?t=413192](http://ubuntuforums.org/showthread.php?t=413192).

I have not tried iansyngin's suggestion. But it might help you guys.

VMR.

---

### Post by Dirty Ole on 2007-04-21
Uninstall previous instances of azureus and install as directed in [this thread]("http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus")

---

### Post by b0ng0 on 2007-04-21
I tried that but it doesn't let me update azureus now as it says it doesn't have sufficient permissions.

EDIT: Nevermind, I looked a few pages into that thread and realised you have to run it as root through the terminal. Not the newest version of Azureus but hey, it works.

THanks

---

### Post by CheetahCat on 2007-04-22
Same here.

I just removed the Azureus on my Feisty and installed it via Automatix ([www.getautomatix.com)](www.getautomatix.com)).

Works just perfect now. :)

---

### Post by b0ng0 on 2007-04-22
Yeh I reinstalled Ubuntu yesterday and I used Synaptic to get Azureus and it seems they have changed the version back to 2.5  in the repos instead of 3.0 which didn't work.

CheetahCat, just curious - what version did you get with Automatix and now works?

---

### Post by vishnumrao on 2007-04-22
> **CheetahCat said:**
> Same here.

I just removed the Azureus on my Feisty and installed it via Automatix ([www.getautomatix.com)](www.getautomatix.com)).

Works just perfect now. :)


Same here. Got Azureus working flawlessly after installation through automatix2.

VMR

---

### Post by schmolch on 2007-04-24
I had the same problem with the internal error msg and rm'ing $HOME/.azureus fixed it for me.

---

### Post by commonplace on 2007-04-30
> **schmolch said:**
> I had the same problem with the internal error msg and rm'ing $HOME/.azureus fixed it for me.

This worked for me as well. Thanks!

/Kevin

---

### Post by cyfex on 2007-04-30
I had similar problems with azureus crashing randomly..
After the first crash the main window would appear and then disappear right away.

I think the problem is related to the sliding alert messages (as mentioned on another thread too).

I cleared the configuration by executing the following on a terminal:
```
rm -r ~/.azureus
```

On the next run of azureus, I checked the "Disable sliding animation/on top style for alert messages" option
under Options -> Interface -> Display.

It seems to be working fine now.

I'm using azureus 2.5.0.0 and the sun-java6-xxx packages from the repos..

---

### Post by commonplace on 2007-04-30
Clearing the configuration is what worked for me, but then it just crashed again later on and I had to do it again... and then again later. I ended up just switching to KTorrent.

I'll try disabling the sliding animation in Azureus and see if that helps, but I think I'm a KTorrent convert for now!

/Kevin

---

