---
title: "Screen goes black even without power management"
date: 2007-10-23
forum: General Help
---

### Post by LocoMan on 2007-10-23
I'm having a weird issue since I installed 7.10.

Basically, every 20 minutes or so, the screen goes black, as if the power management option had kicked in... problem is, I have it set to not use screensaver, and never blank the screen. The power management is off on bios too.

I've tried to set power management to put display to sleep never, or after an hour, it seems to just ignore them and blank the screen after 20 minutes or so. It's kinda annoying since I have 2 computers side by side, a windows one I use for gaming and work, and this one (ubuntu) that I mostly use to keep an eye on IRC, mail, internet and fool around, and it's kinda distracting when I'm concentrating on the other one and this monitor goes black.ç

Any ideas?

Running gutsy 32 bits, upgraded from feisty (that didn't do that), video card is a nvidia 7100.

---

### Post by teutori on 2007-10-24
You should try 'xset s off' in the console.

---

### Post by LocoMan on 2007-10-24
nope.. still does it. I even disabled power manager in the session menu.

Any other ideas?... it's driving me crazy. It doesn't really turns the screen off, it just goes black.

---

### Post by jhunter on 2007-10-24
Take a look at the following page:
[http://www.ubuntugeek.com/workaround-for-feisty-screensaver-bug.html](http://www.ubuntugeek.com/workaround-for-feisty-screensaver-bug.html)

It seems the bug wasn't fixed for Gutsy.  Although, if your a beginner, use gedit instead of vi...just a tip.

---

### Post by LocoMan on 2007-10-24
No luck here... 

Anytime I add one of those it just breaks gnome, logs into failsafe graphics mode and then loses all configuration on video, restircted drivers and keyboard layout (all quickly fixed, though... that failsafe log thing is great, in previous versions I'd been lost when the GUI breaks down).

---

### Post by teutori on 2007-10-26
> **LocoMan said:**
> No luck here... 

Anytime I add one of those it just breaks gnome, logs into failsafe graphics mode and then loses all configuration on video, restircted drivers and keyboard layout (all quickly fixed, though... that failsafe log thing is great, in previous versions I'd been lost when the GUI breaks down).

If you copy-pasted from the previous link to you xorg.conf you should notice that the quote marks ( “ &#8243; ) are not regular quote marks ( " " ). They need to be replaced and your gnome should start normally.

---

### Post by carfinder01 on 2007-10-30
HI I am also having the same problem. I am running ubuntu 7.10. I also have compiz installed. I noticed his started happening after i installed it. ANy clues to what i can do. 
PS please be elaborate im a newbie to Linux:)

---

### Post by supernova_hq on 2008-05-04
I am also having this problem. I also started noticing it after installing compiz. I have recently upgraded from 7.10 to 8.04 and the problem is still there.

I have also gone through every single power and screen saver setting I can find, to no avail.

I looked through compiz (no really thorough though) but have not found anything that would relate to any blank screens, screen savers or monitor power offs.

---

