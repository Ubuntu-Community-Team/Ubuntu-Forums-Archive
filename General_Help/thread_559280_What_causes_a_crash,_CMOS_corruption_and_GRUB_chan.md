---
title: "What causes a crash, CMOS corruption and GRUB changes?"
date: 2007-09-25
forum: General Help
---

### Post by monstermunch on 2007-09-25
Hi,

I'm running Ubuntu 7.04 and it's been running very stable for weeks with no crashes. The other day I was watching a video file in Kaffeine whilst ripping a CD when the computer just froze and I had to do a hard reset. Upon resetting, I got message about my CMOS being corrupted (I was worried!). I went into the BIOS and restored default settings. On rebooting, I then got stuck at "Verifying DMI...".

I tried the Ubuntu live cd and restored GRUB for something to try (I believe this restored my menu.list file from my drive). On resetting, the GRUB screen would appear but none of the options worked. After some fiddling and reading forums posts, I found I could boot normally into Ubuntu on my drive by changing GRUB to boot to (hd1,8) instead of (hd0,8). The Windows entry also had to be changed in a similar way with the addition of:

map (hd0) (hd1)
map (hd1) (hd0)

I don't have a great knowledge of GRUB, but the menu.lst file on my drive hadn't been changed before (or after) my crash. Everything is working now, but I'd like to know if anyone has any idea what exactly happened? I haven't changed my hardware recently, played with GRUB etc. but something about my drive configuration seems to have changed. What would cause my CMOS to get corrupted and this to happen?

---

### Post by tgalati4 on 2007-09-25
Three things come to mind:

1)  Hardware failure

Look for a blister in your Southbridge chip.  If yes, then your motherboard may be toast.

Just because you can do a lot of things simultaneously in Linux (without crashing) doesn't mean it's a good idea.

I'm going to make a guess that watching video and compressing a CD puts double load on your Southbridge chip.  It heats up and lets out the magic smoke.  You're done.

Look into the specs of your motherboard and list all of the functions of your Southbridge chip and tell us which ones you were using at the time of the failure.

2)  Lightning.

3)  Cosmic Ray.


ps:  You have an eMachines. (That's my guess.)

---

### Post by Shazaam on 2007-09-25
I HATE it when I let the smoke out of electronic equipment.
That aside, how old is the motherboard battery?

---

