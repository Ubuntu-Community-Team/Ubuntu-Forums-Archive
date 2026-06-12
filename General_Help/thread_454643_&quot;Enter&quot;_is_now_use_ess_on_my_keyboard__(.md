---
title: "&quot;Enter&quot; is now use|_ess on my keyboard  (so is |_ )"
date: 2007-05-25
forum: General Help
---

### Post by FRuMMaGe on 2007-05-25
Okay so I was trying to configure the specia keys on my computer and pressed enter by mistake.  Even though i changed it right away, it must have overwritten the previous function of it.

Now I have to use the Numpad one which is rather annoying.

Is there a way to revert the keyboard map?

Aso the key between K and ; is broken.  But i cant type it :P ( |_ )

---

### Post by FRuMMaGe on 2007-05-25
Come on guys, this is incredib|_y annoying !

---

### Post by FRuMMaGe on 2007-05-25
bump

---

### Post by dnzz on 2007-05-26
System-->Preferences-->Keyboard Shortcuts

Look there if you changed any shortcut to L and Enter by mistake.

---

### Post by hikaricore on 2007-05-26
Completely off topic, but that is a very nice "poi" still image you got for your avatar there.

---

### Post by richardmclarke on 2007-05-26
I can't help. But I wonder if you can help me. I want to change my old laptop to Xubuntu but the enter button doesn't work. With windows I used a program called keytweak to re-assign the function of other keys to work as an enter button. Before I wipe my laptop can you tell me if you can re-assign key functions with ubuntu 7.04?

---

### Post by rillip on 2007-05-26
Yes, you can reassign keys.  See above from dnzz on how.  You can find more comprehensive instructions out on the net.

As for the L button not working, first off, that makes your post histerical. :D  But in a more helpful veign, are you sure it's not just the key being broken?  I get the impression you press it and nothing happens.  If you've checked your keyboard bindings and don't see a goof for l, you might be able to undo the damage using a configure/purge command, but I can't tell you what one it would be.

For example, it's common to break one's sound when tweaking with it to try and get the right devices working.  In such a case you can run dpkg-configure --purge alsa  to rever to your standard alsa settings.  You could also try and boot from a live CD, find the config file, and paste it over your old one.  Again, I'm not sure what file this would be, but at least it gives you some directions to look.

---

### Post by FRuMMaGe on 2007-05-27
I've found it!

basically you have to go to Applications->System Tools-> Configuration editor, then Desktop-->Gnome-->Peripherals-->Keyboard-->kbd  and delete all values on Layout and Options.

Now I can use the L key again!! LLLLLLLLLLLLLLLLLL

---

### Post by rillip on 2007-05-27
Lol, glad you got the L key working again.  Sounds like your fix might have been a little... over the top, but hey, if everything you're using works the way you want, including the L key, I say we call it a day. ;)  But if you make a post next month saying "I can't get this keyboard bidning to work..." :D

---

