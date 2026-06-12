---
title: "System hanging during boot at &quot;Setting sensors limits&quot;"
date: 2005-06-11
forum: General Help
---

### Post by Zed on 2005-06-11
Last night, following [these directions](http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors), I got sensors working. I'm running XFCE (and had the Sensors plugin running in the panel,) and everything was great. I powered down last night.

This morning, I powered up, didn't pay attention to the system messages, and XFCE launched a bunch of apps to restore my session. The sensors plugin reported plausible temperatures, and seemed to be working.

A while later, my system froze while opening a URL in a new tab in Firefox -- it presented a Accept cookie? box (per my options), I clicked deny, and the system froze rock solid, unresponsive to mouse, keyboard, or power button. I pulled the plug.

On restart, there were a lot of messages about replaying transactions (I use Reiserfs for all my partitions except swap.) Then it hung after "Setting sensors limits", never coming back [OK] or [failed]. It was totally unresponsive, so I pulled the power cord and tried again. Same behavior.

Presumably, I need to boot into safe mode... but what then?

---

### Post by Zed on 2005-06-11
Actually, it hangs when booting into recovery mode, too.

Downloading a Knoppix CD now...

---

### Post by Zed on 2005-06-13
Removing the modules from /etc/modules except lm85, which produces the only results I wanted to display in the XFCE panel sensors plugin did the trick.

---

