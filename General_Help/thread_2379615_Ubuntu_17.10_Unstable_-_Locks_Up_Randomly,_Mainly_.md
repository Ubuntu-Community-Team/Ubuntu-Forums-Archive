---
title: "Ubuntu 17.10 Unstable - Locks Up Randomly, Mainly on Logging In (Dell XPS 15-9560)"
date: 2017-12-07
forum: General Help
---

### Post by mogggiex on 2017-12-07
Howdy,

I have a fresh install of Ubuntu 17.10 that really is not happy :(

After logging in using any of the 3 options (GNOME, Ubuntu or Xorg), 7/10 times **the cursor will lock up and the screen will freeze**.

Once it gets past this lottery, it'll normally run fine, however:


[LIST]
[*]If I leave the laptop alone for 20 mins or so, it'll randomly lock up (become unresponsive)
[*]If I dare plug in the power supply, chances are it'll lock up
[/LIST]

Right now as you can imagine, it's terribly frustrating.

The laptop is brand new, it's a Dell XPS 15 9560. So very well powered hardware-wise & Windows 10 runs absolutely fine (it's a dual boot machine).

I've read other posts where users have found using xorg when logging in resolved it for them, sadly this ins't the case for me, hence the plea for help.

I'll happily run any reports etc you can suggest.

Matt

---

### Post by dragonfly41 on 2017-12-07
I have a Dell 3268 humming along nicely with dual boot Windows 10 and Ubuntu 16.04 plus others as backup.
You will need to do detective work and I have found the utility glogg helps in scanning log files for clues.
Keep different tabs open for different log files to inspect from /var/log.
e.g. kern.log, Xorg.0.log, error.log, syslog ...

Use search facility to look for keywords such as fail, error etc.

---

### Post by rbmorse on 2017-12-07
Mogggiest, what's the video hardware in that machine?

---

### Post by mogggiex on 2017-12-08
Good morning gents!

Last night I got annoyed and installed Ubuntu 16.04 over 17.10. 

Much more stable now, just minor annoyances with the trackpad, but thats nothing compared to system freezes from before.

Kinda resolved the issues myself the extreme way ;)

Matt

---

