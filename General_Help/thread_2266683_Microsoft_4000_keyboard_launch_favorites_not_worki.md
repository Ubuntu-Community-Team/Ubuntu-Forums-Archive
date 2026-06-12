---
title: "Microsoft 4000 keyboard launch favorites not working in 14.04"
date: 2015-02-24
forum: General Help
---

### Post by Slatevine on 2015-02-24
Ive seen a few threads on this, but none seem to help.

Most of the shortcut keys on my Microsoft 4000 keyboard work fine. The favorites # 1-5 do not.

The system setting keyboard shortcut mapping picks them up OK. It correctly sets "switch to workspace 1" to "Launch5" when I press favourite key #1 it for example.

But pressing favorite key #1 does nothing. No workspace switching. (And yes, that is when Im not already on workspace #1!)

If I reassign switch to workspace 1 to ctl 1, for example, it switches correctly. 

I see the favorite keys recognised in xev, which I would expect as they are recognised in the key map settings.

But there's more. I also run a Ubuntu 12 system. On this, the same keyboard with switch to workspace #1 <=> Launch5 works just fine.

So it's a case of spot the difference. But where do I start to look? Unless of course someone already knows the root cause of the problem.

---

### Post by tgalati4 on 2015-02-24
Check the difference for the exact keyboard that is selected in the GUI interface of both systems.  I have a Microsoft 4000 keyboard available to select in my GUI.  Is it selected in both systems?  It's possible that those keycodes (and mappings) were picked up by another application and are not available to the shortcut GUI.

---

### Post by Bucky Ball on 2015-02-25
*Thread moved to **General Help**.*

---

### Post by Slatevine on 2015-02-25
Thanks for the suggestion/reply.

I cant figure out where I specify the keyboard type. I thought maybe in dconf-editor or unity tweak tool, but i cant see anything in there. The help I found was all for earlier versions than 14. Maybe it changed?

---

### Post by tgalati4 on 2015-02-25
I'm running Linux Mint MATE 17 (based on 14.04).  In my Menu-->Preferences-->Keyboard-->Layout Tab-->Keyboard Model-->select Microsoft 4000.

I have that keyboard, but on an older system.  If I have time, I will move it to 14.04 and see if I can assign the extra function keys.

---

### Post by Slatevine on 2015-02-25
when you say menu, you mean System Settings (well in Ubuntu 14 anyway)? That's where Id expect to find it. 

But in keyboard there is only a typing and a shortcuts tab. Nothing Leyout-related.

I have a feeling Im being dumb here. Good job I can hide my embarrassment behind the screen :-).

---

### Post by tgalati4 on 2015-02-26
The console command for me is *mate-keyboard-settings*.  For you perhaps:

```
gnome-keyboard-settings
```

---

### Post by Slatevine on 2015-02-26
I cant find anyh package called either of those. 

I did find [this article.]("http://smallbusiness.chron.com/ubuntu-work-microsoft-natural-keyboard-51245.html")

Running that utility doesn get me much further though. It will recognise all the other keys. But pressing any of the favorites does absolutely nothing. Rather like in system settings.

If I hadnt seen the keys recognised xev I'd think they werent recognised at all and give up. But they are, they just dont do anything.

OK, so to the suggestion something else is intercepting them - how do I start looking for the culprit (given this isnt windows so a reinstall isnt the way!)

---

### Post by tgalati4 on 2015-02-26
If you are running Unity, then try a non-Unity desktop from a LiveUSB stick.  Hook up the network and install *keytouch-editor* and see if you can define the keys.  If so, then you know that there is an issue with Unity grabbing those keys.

---

