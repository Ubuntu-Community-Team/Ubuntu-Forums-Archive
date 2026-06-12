---
title: "Is there a way to..."
date: 2007-04-02
forum: General Help
---

### Post by kryos on 2007-04-02
>While messing with a Beryl installation on an older machine, more trouble was >caused than it was worth.

Format and rebuild turned out to be the surest way to go.
Thanks to all.

---

### Post by maheshjagadeesan on 2007-04-03
I'm no expert, but I could try helping if you would tell us what exactly is wrong now. Going by your reference to xorg, should we assume X is broken?

---

### Post by heimo on 2007-04-03
> **kryos said:**
> Is there a way for Dapper to look at hardware like it did during initial setup and make changes accordingly?  While messing with a Beryl installation on an older machine, more trouble was caused than it was worth.  Cannot maximize some programs windows/cannot run some screensavers or system will lock up requiring a hard boot.  I can modify xorg but have no idea to what.

You could try "undoing" what you did to get beryl working. If it's still running and causing most of the problems, and it's set to start automatically, remove it from your session, log out and log in. That's what I'd try first.

---

### Post by Spr0k3t on 2007-04-03
To "get beryl working" what steps did you follow.  I'm sure there is something in there where you can disable a setting or update a driver to get the functionality back to where you started with.  Also, what graphics chipset?

---

### Post by kryos on 2007-04-03
[http://www.biodesign.com.ar/blog/?p=16](http://www.biodesign.com.ar/blog/?p=16)
This was attempted prior to the notice "Beryl is not supported on Dapper Drake anymore (March 2007)"
Additionally, xorg has been reset to the ati driver, etc. by following the comments at the beginning of the file and beryl has been removed through Synaptic.
Radeon® 7000 / Radeon® VE  (R 100)

---

### Post by kryos on 2007-04-03
> **maheshjagadeesan said:**
> I'm no expert, but I could try helping if you would tell us what exactly is wrong now. Going by your reference to xorg, should we assume X is broken?

As stated, Cannot maximize some programs windows/cannot run some screensavers or system will lock up requiring a hard boot.
No, X is not broken. Maybe cracked or dented a little.

---

### Post by kryos on 2007-04-03
> **heimo said:**
> You could try "undoing" what you did to get beryl working. If it's still running and causing most of the problems, and it's set to start automatically, remove it from your session, log out and log in. That's what I'd try first.

The above has been done previously.  Will look at your link in depth this evening.  Thanks.

---

### Post by Spr0k3t on 2007-04-04
> **kryos said:**
> Radeon® 7000 / Radeon® VE  (R 100)

Sorry to say, but I'm not expert on ATI.  I read too many issues regarding ATI and linux in general that I made the switch to nVidia on my primary system to avoid the hassels.

---

### Post by maheshjagadeesan on 2007-04-04
> **kryos said:**
> As stated, Cannot maximize some programs windows/cannot run some screensavers or system will lock up requiring a hard boot.
No, X is not broken. Maybe cracked or dented a little.

This is probably an extreme suggestion, but I'd think that removing X completely and then reinstalling it should resolve the problem; removing it completely would ensure that the screwed-up configuration files will be replaced when you install it again.

Alternatively, you could try one of the following:
a. Try compiz by adding the compiz repository to your sources
b. Use xf86config or Xconfigurator to manually reconfigure your X settings.

HTH.

---

### Post by kryos on 2007-04-04
Thanks to all that have made suggestions.  It is appreciated.  Even after doing the whole "sudo dpkg-reconfigure xserver-xorg" thing from the excellent link in heimo's post,  I'm still having the same problems.  It is looking more and more like rebuild time!

---

