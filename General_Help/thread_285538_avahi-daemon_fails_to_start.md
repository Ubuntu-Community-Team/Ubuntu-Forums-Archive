---
title: "avahi-daemon fails to start"
date: 2006-10-26
forum: General Help
---

### Post by shamael on 2006-10-26
After quite a lot of trial and error I've found out why my daap shares had disappeared (ages ago :(): avahi doesn't start anymore! Invoking the startup script from the terminal gives no output whatsoever for commands start, reload, status.
On the other hand, using stop fails (of course, but at least I get some output from the script!).
Oh and yes, I have tried reinstalling avahi.

Any idea on how to troubleshoot this?

---

### Post by beerfan on 2006-10-26
> **shamael said:**
> After quite a lot of trial and error I've found out why my daap shares had disappeared (ages ago :(): avahi doesn't start anymore! Invoking the startup script from the terminal gives no output whatsoever for commands start, reload, status.
On the other hand, using stop fails (of course, but at least I get some output from the script!).
Oh and yes, I have tried reinstalling avahi.

Any idea on how to troubleshoot this?

I've only seen Edgy from the cd booter so far but look in the Services manager and you should see an avahi service there. It was not enabled by default for the cd booter but in the regular install...who knows.

---

### Post by magicfab on 2006-10-26
It's difficult to help without knowing if you use Dapper / Edgy, and what application(s). How did you reinstall ? What package(s) ?

---

### Post by shamael on 2006-10-27
I am using edgy now, but I had the same problem in dapper before, only I didn't have time to work on it.
I need avahi to access my daap shares with rhythmbox.
I reinstalled avahi-daemon, avahi-utils and avahi-discover through aptitude.
Technically, I wanted to purge-uninstall avahi-daemon and then reinstall it, but aptitude said that the latter two depended on the daemon and on ubuntu-desktop as well. As far as I remember ubuntu-desktop is a meta-package so it's safe to remove it but I didn't want to break anything so I simply reinstalled those three.
Also, to answer beerfan if I go in BUM and try to enable avahi-daemon nothing happens (I mean that avahi doesn't start at all).

---

### Post by mrashley on 2006-10-28
I'm using a fresh Edgy installation and I'm having the same problem. I can ```
sudo avahi-daemon &
``` to start it up manually, but it's supposed to start with the system.

It may be significant in troubleshooting that I found if I typed ```
sudo /etc/init.d/avahi-daemon stop
``` that gave me the output of ```
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ fail ]
``` but if I tried to ```
sudo /etc/init.d/avahi-daemon start
``` it would merely return the prompt.

---

### Post by spd106 on 2006-10-28
Open the network-admin tool, go to the general tab, and tick the box under Automatic Service Discovery.

This worked for me.

I believe there is another way by putting a 1 in a config file somewhere, but this is the simplest option for most people.

---

### Post by shamael on 2006-10-28
Now, that's interesting... if you run the network-admin tool from the command line and tick that box, you can see in the terminal:

```
* Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ ok ]
```

(...or something like it, I'm not in Ubuntu right now.)

And that's exactly what the script should output!
Maybe there's some flag in the script that prevents it from starting avahi if that box is not ticked? I tried to check it out but I'm not that linux-savvy...



On a sidenote, if that weren't to work one could always do```
sudo avahi-daemon -D
``` to start and```
sudo avahi-daemon -k
``` to stop avahi...

---

### Post by foxer on 2006-10-28
try editing /etc/default/avahi-daemon set AVAHI_DAEMON_START=1

---

### Post by shamael on 2006-10-30
Aha! Thanks foxer, that made /etc/init.d/avahi-daemon return to normal behavior.
Now I'm curious though, why is it useful to have a startup script that can be disabled by some other configuration file? Wouldn't it be easier to either have an "on-off" option within the script itself or a centralized master .conf with all the enabled and disabled startup scripts (which I thought is the way BUM works)?

---

