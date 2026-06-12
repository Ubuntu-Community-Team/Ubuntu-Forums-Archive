---
title: "Fix for Firefox in Edgy: Downgrade to 1.5!"
date: 2006-11-01
forum: General Help
---

### Post by traneHead on 2006-11-01
If anybody has had the same freezing experiences like I have had with Firefox 2.0 (final!) on Edgy (also final) and haven't succeeded with any or all of the tips posted here before (setting X to 24 bit mode - already had that, adding "export XLIB_SKIP_ARGB_VISUALS=1" in /etc/firefox/firefoxrc, removing all extensions and plugins... ...), here's a link to download Firefox 1.5:
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.7/linux-i686/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.7/linux-i686/)

I haven't figured out what was causing the freezes (extensions?, plugins?, the firefox binary or libs?), but now with the 1.5 the flash9 plugin works, java5 plugin works, totem plugins works as well as my extensions.

I've installed it in my home dir for now, so that the official version is kept in /usr/bin (so that it can get updated and hopefully fixed), and just changed the paths in the gnome shortcuts and menus.

Also, doesn't it suck that the  session-manager in 2.0 only works if you've had a crash? I need to be able to store and restart a browsing session deliberately, without having to "pkill firefox"... The session-manager extension ([http://sessionmanager.mozdev.org/](http://sessionmanager.mozdev.org/)) was perfect, but it doesn't work with 2.0... I know this isn't an Ubuntu issue, but since I'm already whining... ;)

---

### Post by Zeroangel on 2006-11-01
Session manager works even if you dont have a crash, all you have to do is enable it by going to preferences -> main -> "When firefox starts" -> Show my windows and tabs from last time.

---

### Post by traneHead on 2006-11-01
OK, thanks! Missed that one.

---

### Post by hikaricore on 2006-11-01
You are using firefox and not swiftfox correct?  I had to update the launcher scripts for both on my system to make them stop crashing, since the firefox startup script is ignored by swiftfox.  :)

---

### Post by yopnono on 2006-11-01
Why install the official FX 1.5, and not the official 2.0 instead?

---

### Post by bluenova on 2006-11-01
Personally I would say downgrade to V2.0 RC2 as it's quicker that 1.5 and it seems to be the most stable.

---

### Post by traneHead on 2006-11-01
> **yopnono said:**
> Why install the official FX 1.5, and not the official 2.0 instead?

Because it froze too...

---

### Post by yopnono on 2006-11-01
> **bluenova said:**
> Personally I would say downgrade to V2.0 RC2 as it's quicker that 1.5 and it seems to be the most stable.

What? Do you think that the RC2 is better then the final 2.0 from Mozilla.
I use the Official Fx from mozilla, and it works great.
(Not talking about ubuntu FX)

---

### Post by traneHead on 2006-11-01
> **hikaricore said:**
> You are using firefox and not swiftfox correct?  I had to update the launcher scripts for both on my system to make them stop crashing, since the firefox startup script is ignored by swiftfox.  :)

hmmm, yes I'm using FF, not Swiftfox (that I've never heard of). OK, so the startupscript would be /usr/bin/firefox right? So this isn't updated by going from 1.5 to 2.0? But it should be? Hmm, time to fill in a bugreport i guess.

Thanks for the suggestion!

---

### Post by bluenova on 2006-11-01
> **yopnono said:**
> What? Do you think that the RC2 is better then the final 2.0 from Mozilla.
I use the Official Fx from mozilla, and it works great.
(Not talking about ubuntu FX)
Yes, having used each development version as they came out, RC2 seemed to be the most stable.

---

