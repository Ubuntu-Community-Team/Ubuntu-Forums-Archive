---
title: "No jack sense in quantal"
date: 2012-11-07
forum: General Help
---

### Post by lykwydchykyn on 2012-11-07
I've got a Dell optiplex 580, with an AMD Azalia sound chip.  In Precise my audio worked fine and as expected, but after upgrading to quantal "jack sense" doesn't seem to work:  in other words, when I plug in the headphones the speakers don't shut off.

pavucontrol doesn't show more than just the one hardware output, so I can't separately mute the speakers.  If I mute the output, both speakers and headphones stop.

Any advice?

---

### Post by lykwydchykyn on 2012-11-07
OK, I thought it was fixed, but it's not now.

After replacing my /etc/pulse/default.pa with the dpkg-dist version provided by the upgrade, it detects if I have the headphones plugged in, but instead of cutting off the external speakers (plugged in the back), it just cuts off the built-in speaker and boosts the volume of both the headphone output AND external speaker output.

So, in effect, plugging in headphones makes my speakers louder. :|

---

### Post by lykwydchykyn on 2012-11-07
Fixed it.

In case anyone else has this issue:

 - Open a terminal
 - run alsamixer
 - hit 'F5' to see advanced controls
 - Look for the "auto mute" setting.  It's probably disabled.
 - Arrow over to it, and arrow up to set it to "line out"

---

