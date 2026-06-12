---
title: "Flash Player Firefox 3 beta 5 and RC1 Hardy Heron BIG PROBLEM"
date: 2008-05-31
forum: General Help
---

### Post by huczek on 2008-05-31
I still have problem with flash player.
After closing tab with page with embed flash in terminal it returns an error:
```
(firefox:8512): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```
and somethimes crashes.

with flash player 10 beta it's
```
(firefox:6773): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6773): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

I used the advice from thread about SCIM [http://ubuntuforums.org/showthread.php?t=757070](http://ubuntuforums.org/showthread.php?t=757070)
I used advices about flash player 10 beta about flash player 9 and libflash support etc. Of course always I used 1 version of flash and libflashsupport only with default - nonfree Adobe Flash Player 9.0.124.0ubuntu2.

I tried many options:
Firefox 3 beta 5 with flash 10 (after flash 9 uninstalled)
Firefox 3 beta 5 with flash 9
Firefox 3 beta 5 with flash 9 with libflashsupport 
The same with Flash 3 RC1

The only chance to avoid the error is to turn off the flash player plugin in ff.

I use Hardy Heron 8.04 stable LTS x86 32 bits.

I've been trying for one week and still looking for a solution.

---

### Post by shifty_powers on 2008-05-31
have you tried gnash?

---

### Post by Mhurst1 on 2008-05-31
Thats a mozilla issue report it to them.

---

### Post by huczek on 2008-05-31
> **shifty_powers said:**
> have you tried gnash?

no I haven't

in my opinion it is a problem with flash player. After turning off the flash plug in, there's no error message, But I'm not sure if it is directly the flash that causes the problem.

---

### Post by huczek on 2008-06-05
Has anybody an idea?

in firefox 3 RC2 the same error occurs after closing tab or browser window with page containing flash
```
(firefox-bin:8588): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

---

### Post by huczek on 2008-06-05
Still no help in this field. A clue. In seamonkey with the same set of plugins there is no such a problem.

---

### Post by ilcavero on 2008-06-05
this is the most annoying bug right now with hardy along with the pixelation on videos with ATI cards and Glipper failing to load. :mad: I'm about to throw the towel with hardy and try other distro.

---

### Post by huczek on 2008-06-06
Yep! The problem is firefox 2 crashes, firefox 3 is beta, and even rc 2 is not stable. seamonkey isn't fully supported via system as a default browser i.e.: thunderbird's links aren't open 'till you manually run seamonkey.

[COLOR="Blue"]**OT:**
Another problem... display doesn't put to sleep sometimes. I'm afraid there are more issues that can be even harmful for my hardware like harddrives. The huge ubuntu community isn't helpful enough. That's a problem number 1 in my opinion. There should be number of solutions which help in problems with hardy, but the information flow is not efficient. I'm really disappointed by Ubuntu. It works like beta system and the version is marked LTS [Long Term Support]. I remember problems with previous LTS. It looks like other non-LTS distros are more stable like 7.10 or 7.04.[/COLOR]

---

### Post by huczek on 2008-06-18
> Another problem... display doesn't put to sleep sometimes.
well it looks like the same problem. the flashplayer and firefox 3 (current, stable) cause the mentioned error (in the terminal GLib-GObject-CRITICAL) and the display doesn't put to sleep. 

Anybody?

---

