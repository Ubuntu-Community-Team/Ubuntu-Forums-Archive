---
title: "Getting message &quot;Pending update of 'deja-dup&quot; snap...'"
date: 2022-06-24
forum: General Help
---

### Post by astronomertom on 2022-06-24
"Close the app to avoid disruptions (12 days left)"

This message has been popping up in my notifications the past few days now on my Ubuntu 20.04 system.  Could not find any details via online searches, so I'm asking here.

Just what does it mean?  I run Software Update regularly so what is so different about this update?

The app is normally closed except when I run backups.  Is there anything else I need to do?

Thanks,
WTB

---

### Post by TheFu on 2022-06-24
snap updates aren't part of the APT updates.

snap updates default to checking daily. You can modify the snap update period using snap commands, among other things.  I have snaps set to only check for updates on Saturdays to prevent disruptive updates, for example.  [https://snapcraft.io/docs](https://snapcraft.io/docs)  has all the commands and options for snap package management.

Yes, it would be better if snaps, flatpaks, and appimages were fully integrated into the APT package management tools on Ubuntu and it would be better if we could prevent snaps from being used at all by default.

---

### Post by Naturally-Simple on 2022-06-25
I've been getting the exact same message. TheFu, you didn't really answer the OP's question, which is mine too: What does this notification mean?

Yes, I'm aware of how snap updates are different, so I've heard, but I've never had notifications like this for anything else before, which could be the OP's reason for starting this thread. What changed that we now get this notification after previously never getting it or any other snap update notifications?

---

### Post by TheFu on 2022-06-25
If you have an issue, start your own thread and ask your own question. "Me Too" posts aren't really how these forums work. Definitely link to this thread if you have
exactly the same issue, 
with exactly the same OS,
with exactly the same software,
with exactly the same hardware.

snaps are a completely different package system. They automatically update. There are no notifications on any of my systems when they update.  Without the exact log message, nobody can help. Web-search for 'ubuntu logs' to find where those are and how to search them.

---

### Post by Holger_Gehrke on 2022-06-25
According to [this part in it's documentation]("https://wiki.gnome.org/Apps/DejaDup/Details#Scheduling"), 'deja dup' uses 'deja-dup-monitor' to run scheduled backups instead of the system wide scheduler cron. If any program from a snap is running while a refresh is attempted, you will get a notification (I've seen that multiple times with firefox ...). So you probably need to stop deja-dup-monitor. Since I don't use deja-dup, I can't tell you the right way to do this, but I'd look at 'snap services' first. If it's listed there you can use 'snap stop' with the name of the service and then do the update with 'snap refresh'. Otherwise I'd look for a systemd service or an autostart item.

Holger

---

### Post by orduek on 2022-06-26
I had the same issue, this is how I solved it.
1. First, search for the dejadup monitor PID
    pidof deja-dup-monitor

2. Stop dejadup monitor
   sudo kill -9 <enter relevant PID here>

3. sudo snap refresh

---

### Post by TheFu on 2022-06-26
So, the root issue is that snap which run as daemons need special update methods.  I use lxd 24/7 and have a years now. It is distributed only as a snap package, so when it updates, I'd notice any errors. There are none ... well ... none like this thread describes, so I can only assume they are handling the upgrade in some way that makes it work while running OR just delays using the newer code until a reboot.  

Until deja-dup does something similar, the fix would be not to use the snap version of the code.  It appears there is a non-snap package still, so I'd use that instead.
```
$ apt search deja-dup
Sorting... Done
Full Text Search... Done
deja-dup/focal-updates 40.7-0ubuntu1 amd64
  Backup utility

```
I looked at the APT dependencies and there aren't any snap package dependencies, so I really think using the snap is 100% optional.

---

### Post by guiverc on 2022-06-26
The ***days left*** is a counter before the package will be forced closed; so the update of the package can occur.  The default count is 14 days, so if it's saying *12 days*, I would read that as the newer package was detected about 2 days prior.

When the program isn't running, use

```
snap refresh
```

to force the snap package to refresh when it's not being used.  I find that handy, before I start my browsers to avoid getting notifications that I need to close it in order to refresh (*there was a recent bug report on this issue, alas I can't currently find it*).

---

### Post by astronomertom on 2022-06-27
So I appear to have a couple of options for resolving this.
It was such a confusing message to see, since I routinely check for updates.

Thanks.

---

### Post by TheFu on 2022-06-27
> **astronomertom said:**
> So I appear to have a couple of options for resolving this.
It was such a confusing message to see, since I routinely check for updates.

Thanks.

Checking for updates too often isn't good, but many people do this.  "New" is the enemy of "stable."  My systems don't check more than once a week. Actually, I don't let APT look for updates, ever, so every weekend, I run a script to update, upgrade, and remove any unwanted snaps.

---

### Post by kc7zdm on 2022-06-27
Thanks! I had this question for the snap store. Just successfully refreshed that.

---

