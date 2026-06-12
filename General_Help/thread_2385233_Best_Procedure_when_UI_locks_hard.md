---
title: "Best Procedure when UI locks hard"
date: 2018-02-18
forum: General Help
---

### Post by bobnn on 2018-02-18
I'm running Ubuntu 14.04 with a somewhat dodgy install of the GUI.  For instance, I'm running a gnome-flashback interface, but apt-cache policy gnome-flashback-desktop says it's not installed.... and I've used plenty of PPAs......(which I've heard is a bad idea...)

Anyhow, every once in a while the GUI completely freezes - today I couldn't even get a terminal with Ctrl-Alt-F2.

So I ssh'd into the box as root and scheduled a reboot:

```
at now + 2 minutes
shutdown -r now
(ctrl-D)

```

The machine rebooted - but upon reboot, it needed to fsck /home - which surprised me.

So, my question is:  would I have been better off with:

```
Alt-PrintScreen R E I S U B
```

assuming that I could have actually done it?

Would that have been more likely to get a clean umount?

---

### Post by DuckHook on 2018-02-18
gnome-flashback-desktop is a metapackage. This means that it is just a wrapper for a whole slew of apps, libraries and services that make up what we think of as a "desktop" experience. For example, it will likely drag in Libreoffice, Thunderbird and Firefox among many other apps and tools. You are probably not actually running gnome desktop per se, but the gnome environment in lieu of Unity. Can't tell because we have no idea how or what you downloaded.

Mixing environments is not a good idea. Their config files are different and they sometimes store things in different places. Some people have good luck doing so, but we get enough trouble on these forums from people who have not succeeded that I don't recommend it. If you must have gnome in lieu of Unity, I suggest installing Ubuntu-mate (which is Gnome 2), or Ubuntu-Gnome. Both flavours are built to work natively with the underlying OS and have far fewer potential conflicts.

PPAs are even worse. I highly discourage them. A lot of dependency-hell that people find themselves in can be attributed to their addition of PPAs. Because you've added so many (though we don't know what constitutes "many" or what those are either) you can start your detective work by eliminating them one by one to see if your GUI freezes go away. You will have to be patient because it must be done one at a time with enough testing to exercise your system thoroughly.

If you can ssh in, then the problem is GUI related and not kernel related. This is good. You should be able to review your logs through ssh to see if anything obvious jumps out at you.

The choice between ssh and a proper shutdown vs. REISUB is obvious to me: you always want to shut down properly if possible. REISUB should be a second-to-last resort (with pulling the plug being an absolutely last resort).

Last, but not least, there is a possibility of HW failure. A bad disk or bad RAM could also give the symptoms that you describe.

---

### Post by bobnn on 2018-02-19
> **DuckHook said:**
> gnome-flashback-desktop is a metapackage. This means that it is just a wrapper for a whole slew of apps, libraries and services that make up what we think of as a "desktop" experience. For example, it will likely drag in Libreoffice, Thunderbird and Firefox among many other apps and tools. You are probably not actually running gnome desktop per se, but the gnome environment in lieu of Unity. Can't tell because we have no idea how or what you downloaded.

Mixing environments is not a good idea. Their config files are different and they sometimes store things in different places. Some people have good luck doing so, but we get enough trouble on these forums from people who have not succeeded that I don't recommend it. If you must have gnome in lieu of Unity, I suggest installing Ubuntu-mate (which is Gnome 2), or Ubuntu-Gnome. Both flavours are built to work natively with the underlying OS and have far fewer potential conflicts.

I think I did this before GnomeUbuntu was official. And before Ubuntu-mate was a thing.  

> **DuckHook said:**
> PPAs are even worse. I highly discourage them. 

Everybody does.  But I hadn't seen much of that when I stated using them.  

> **DuckHook said:**
> If you can ssh in, then the problem is GUI related and not kernel related. This is good. You should be able to review your logs through ssh to see if anything obvious jumps out at you.

The choice between ssh and a proper shutdown vs. REISUB is obvious to me: you always want to shut down properly if possible. REISUB should be a second-to-last resort (with pulling the plug being an absolutely last resort).

Yeah, I was just surprised that it wasn't quite a proper shutdown, what with the /home filesystem needing a fsck. 

> **DuckHook said:**
> Last, but not least, there is a possibility of HW failure. A bad disk or bad RAM could also give the symptoms that you describe.

Thanks!  You just reminded me -  the last time I was seeing this, it turned out to be a bad mouse, of all things - there were very frequent USB reset messages in the logs.  And I have noticed some weird occasional lagging with the current mouse.  So I'll have to look out for that.

---

