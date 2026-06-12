---
title: "should I upgrade to gutsy?"
date: 2007-09-30
forum: General Help
---

### Post by peabody on 2007-09-30
Since the gutsy release is just around the corner, I was interested in upgrading to it because I've heard it has the following features:

[LIST]
[*]Tickless Kernel (low power consumption, I'm on a laptop, so that's a big deal)
[*]Xorg 7.3 (hotpluggable dual setup for external VGA, again, a big deal for laptop users)
[/LIST]

I'm just curious what the state of X is for intel video drives (specifically with a widescreen laptop, should I uninstall the 915resolution package?).  Also, I just setup Feisty on this laptop in the last week.  It took a fair amount of work, but I now have it performing about 99% of what I want.  The only issues are with the Microphone, and the fact the dual-head setup for X is hacky (but I'm happy with it for the most part).  What kinds of things could I expect to go wrong with the upgrade?  Will it hose my ndiswrapper setup for my Broadcom card forcing me to do it again?  How buggy is gutsy these days?

---

### Post by liquidfunk on 2007-09-30
In terms of buggy. My wireless is a bit tempermental. I'm using a RT73 USB card. 

 No sound either? Might just be me?

 I'm not trying anything major at the moment, as it is only a beta. I would stick with what you have, then do a fresh install.

---

### Post by Royel on 2007-09-30
Remember you can always try it on a LiveCD first to get an idea about it.

---

### Post by walkerk on 2007-09-30
The only problem I had was with my Intel 945GM video. The intel driver is recognized and the correct resolution is used once (and only after) gnome is loaded. At boot and GDM the resolution was blurry. I use Openbox and I would have to set the resolution manually after each login with gnome-display-properties... needless to say thats a show stopper. I used 915resolution to get the correct resolution at boot-up.

The new Intel driver seems to only work within gnome whereas with Feisty once I installed it the resolution was set from boot up. Minor issue but irratating nonetheless.

Other than that small issue Gutsy works great. If you want the kernel w/out upgrading you can check out my signature...

---

### Post by peabody on 2007-09-30
> **Royel said:**
> Remember you can always try it on a LiveCD first to get an idea about it.

Yes, well, in my case my machine takes a bit of work to get setup out of the box correctly.  Running the LiveCD isn't going to tell me what would and wouldn't work.  I'm using lots of extra stuff, getting my wireless working via ndiswrapper via the broadcom drivers, my laptop's widescreen resolution requires additional packages (if I use the i810 driver which is the more stable one), etc, etc.

Although, I suppose you have a point, these are assumptions I'm making about the machine from a feisty background...who knows!  Maybe they work out of the box in gutsy now, I'll give it a shot.

---

### Post by walkerk on 2007-09-30
> **peabody said:**
> Yes, well, in my case my machine takes a bit of work to get setup out of the box correctly.  Running the LiveCD isn't going to tell me what would and wouldn't work.  I'm using lots of extra stuff, getting my wireless working via ndiswrapper via the broadcom drivers, my laptop's widescreen resolution requires additional packages (if I use the i810 driver which is the more stable one), etc, etc.

Although, I suppose you have a point, these are assumptions I'm making about the machine from a feisty background...who knows!  Maybe they work out of the box in gutsy now, I'll give it a shot.

i810 w/ 915resolution. I had to completely remove xserver-xorg-video-intel & xserver-xorg-video-all. This is supposed to be fixed in Gutsy.. Let me go check for a bug on launchpad.

---

### Post by peabody on 2007-09-30
> **walkerk said:**
> i810 w/ 915resolution. I had to completely remove xserver-xorg-video-intel & xserver-xorg-video-all. This is supposed to be fixed in Gutsy.. Let me go check for a bug on launchpad.

That would suck for me.  One of the primary reasons I would even consider upgrading is for additional X functionality.  There's supposed to be a graphical X tool that can dynamically setup the external display if I'm not mistaken.  If that isn't working, the only incentive for me to upgrade to gutsy is the tickless kernel, and as you said, you can apparently get that in feisty.

---

### Post by peabody on 2007-09-30
Well, I'm back from checking out gutsy beta live cd and I'll say it's promising looking.  While it didn't start in the widescreen resolution, I could change my laptop resolution to 1280x800 through the screen resolution control panel.  Compiz and video playback seemed to be working out of the box (which is a big issue in my feisty install right now).  I think the compiz setup is pretty nice, flashy, but not over the top.  One of the things I didn't try was suspend.  Suspend with compiz seems to intermittently fail for me in feisty.

I tried the new screens and graphics administration control panel, but it didn't seem to work :( for me.  Tried to setup a dual display, but that made the X desktop close, after which it used a clone display, where the resolution was right on the external, but the aspect ratio was cut off on the laptop LCD.  Sound had the same issues as feisty did (works, but laptop speakers are not muted when headphones plugged in) which probably means the snd-hda-intel module wasn't being given the proper parameters.

I think I'm going to forgo looking at gutsy until after the release.  I'll be interesting in seeing if dual display for intel adapters is actually made easier or not.

---

### Post by JoeMcC00L on 2007-10-03
It's a wise decision to wait. I am using the intel 915 graphics chip, and had a swell time with it under feisty running beryl. Unfortunately the upgrade to gutsy killed that, and like a noob I forgot to backup my xorg.conf file. I think there are some troubles with the intel graphics drivers that are still being worked out before the release.

Anyhow, congrats on your decision. It might have just saved you a world of frustration.

Joe

---

### Post by dpar on 2007-10-03
I'm using Gutsy now and it seems pretty stable, but the final is just around the corner(a couple of weeks away).

I'd wait if I were you.

---

