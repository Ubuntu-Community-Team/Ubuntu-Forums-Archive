---
title: "Keyboard that changes some of it's keycodes from time to time..."
date: 2005-05-17
forum: General Help
---

### Post by dilerra on 2005-05-17
I got a strange problem.

I want to bind a specific media key on my Logitech DiNovo to a particular action. This usually is OK by editing "/etc/X11/xkb/symbols/inet" and inserting the appropriate keycodes collected with the "xev"-command, together with what ever they should send along (e.g. "XF86AudioMedia" or similar).

Now, my keyboard seems to change keycodes from time to time. Some times, the media key "VOLUME UP" is assigned keycode 176, another time 161. This makes it very hard binding keys...

Has someone experienced something similar?

Thanks in advance / Mattias

---

### Post by ajm2005 on 2006-10-24
I'm experiencing the exact same thing with the exact same keyboard. :( it is rather odd. did you ever work out what the problem was?

---

### Post by ajm2005 on 2006-10-25
I found a fix for this. The problm is a duplicate entry in /etc/X11/xkb/symbols/inet for XF86AudioRaiseVolume (keymaps 175 and 176) in logitech_base key bindings (this causes problems because no keysym can have two keycodes):

...

// Logitech

// Logitech common definitions
partial hidden alphanumeric_keys
xkb_symbols "logitech_base" {

	...

	key <I24> { [ XF86AudioStop ] };
	key <I2E> { [ XF86AudioLowerVolume ] };
	key <I30> { [ XF86AudioRaiseVolume ] };
	key <I32> { [ XF86HomePage ] };
	...

};


Lots of people have reported this bug apparently, eg:
[https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/37341](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/37341)


To fix, you can delete the duplicate volume raise entries in the base configuration, and add in a separate section for your dinovo keyboard, eg:

// Logitech di novo cordless keyboard
partial alphanumeric_keys
xkb_symbols "logidmd" {
    include "inet(logitech_base)"

key <I12> { [ XF86Sleep ] };
key <I02> { [ XF86HomePage ] };
key <I6C> { [ XF86Mail ] };
key <FK17> { [ XF86Search ] };

key <I22> { [ XF86AudioPlay, XF86AudioPause ] };
key <I24> { [ XF86AudioStop ] };
key <I10> { [ XF86AudioPrev ] };
key <I19> { [ XF86AudioNext ] };

key <I30> { [ XF86AudioRaiseVolume ] };
key <I2E> { [ XF86AudioLowerVolume ] };
key <I20> { [ XF86AudioMute ] };
key <XFER> { [ XF86AudioMedia ] };

};


You also have to add the new keyboard in various other config files, as detailed in section 3 here:
[http://forums.gentoo.org/viewtopic-t-231506.html](http://forums.gentoo.org/viewtopic-t-231506.html)
(I skipped the entries for symbols.dir files and the bits pertaining to the mouse)
(after rebotting, gnome complains that it's settings are different to x server settings - choose option to keep x server settings)

Here's another expplantion/ description of the problem, it seems to have irritated many people over the months/ years :)
[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg45427.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg45427.html)

---

