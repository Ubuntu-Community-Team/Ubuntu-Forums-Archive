---
title: "[SOLVED] A few Gutsy issues that I've been dealing with..."
date: 2007-11-29
forum: General Help
---

### Post by k1dicarus on 2007-11-29
First off, let me say that I--like everyone else here--heart Ubuntu. I've been using regularly on my Toshiba Satellite M45-S359 Laptop since Feisty. There are just some issues, bugs, whatever, that have been thorns in my side with this new release.. and I was just wondering if anyone else has been experiencing the same..

1. My wife's laptop is an XP machine. She picks up a decent wireless signal from our apartment, and can connect to it without any problem. My laptop will pick up this same signal (and more) but cannot connect to it. Ubuntu is demanding that I enter a WEP key. The odd thing here is that my wife's laptop connects just fine with no hassle, no prompt for WEP.. (also, this one time about three days ago when my tosh actually did connect for a few hours.. and then disconnected, never to reconnect. All the while the XP machine was connected!) I've tried manually connecting to the network, tried killing my wireless and turning it back on, and have scoured the internets to no avail. Maybe this is just because Ubuntu is so awesomely secure. It's still aggravating, though.

2. My Gutsy has not updated one single time since I performed the upgrade. Upgrade manager is in my startup, and I even opened the manager manually and it insists that my system is up to date. Have there really been no updates since the release??

3. My login screen is jacked. Well.. actually, everything looks fine until I type in my name/pass but the letters are so big when I do that I can't even read what I'm typing (I think I saw another fellow with that issue on here a bit ago).

4. My SNES Emulators quit working, too :( The were fine just after the upgrade, but have randomly quit since. They just crash to nothingness on starting.

5. DeVeDe was working great for about a week, then it started creating some very strange DVDs.. cracking sound and lines/bars through the picture.. far below viewing quality.

I guess since I've just been using Ubuntu (actually, Linux of any sort) since Feisty, things are bound to go wrong.. I'm still going to stick it out.. but any help or comments would be greatly appreciated.

---

### Post by PmDematagoda on 2007-11-29
Concerning your second question, could you post result of:-

```
cat /etc/apt/sources.list
```

---

### Post by k1dicarus on 2007-11-29
Okay, I'm having to use the XP machine right now, so it's kind of hard to copy/paste some of that info, but one strange looking thing I'm seeing when I enter that command is:
 "Line commented out by installer because it failed to verify"
I'm seeing that a LOT..
Sorry I can't just copy paste..

---

### Post by PmDematagoda on 2007-11-29
It seems that the upgrade did not go that well for you, why don't you do a clean install? That could solve most or maybe all of your problems.

---

### Post by k1dicarus on 2007-11-29
I was afraid of that.. ugh. Is there any way to fix that issue besides a clean install? I remember when I was installing and I did not have an internet connection.. and I bypassed the initial update..

---

### Post by PmDematagoda on 2007-11-29
From the problems you are having, you will have a long way to go in order to fix the Ubuntu upgrade and even that cannot be guaranteed.

So your best bet would be to do a clean install of Ubuntu.

---

### Post by k1dicarus on 2007-11-29
Alright, will do. Thanks a lot for your help on that.

---

### Post by jocko on 2007-11-30
> **k1dicarus said:**
> "Line commented out by installer because it failed to verify"

That could happen if you don't have an internet connection when you install.
Open up synaptic (System-->Administration-->Synaptic).
In synaptic, go to settings-->repositories. If you have the problem I think you have you'll see that none of the repos are activated. Activate all repos and try again.

---

### Post by k1dicarus on 2007-11-30
Alright, I opened System>Administration>Software Sources
I clicked the 'Updates' tab
and under 'Ubntu Updates'...
NONE of them were checked..
So, I checked them all.. if that does it, then awesome.. if not, then drat.

---

### Post by k1dicarus on 2007-11-30
Fixed! I, in some finaggled, ragtag way of working around the network manager, got my internet up, then got my updates (200-and some odd MB), THEN I got..... WIDGETS!! ...okay.. not that exciting, but thanks for your help. guys. I guess I just had to check the boxes in my software sources window. My emulators still aren't working, but I'll save that for another day.

That's one thing I love about Ubuntu.. it's so sweet. It'll give you trouble, and you'll get frustrated, but you just know it's so sweet that it'll be worth it once you solve the problem.. double the satisfaction.

---

