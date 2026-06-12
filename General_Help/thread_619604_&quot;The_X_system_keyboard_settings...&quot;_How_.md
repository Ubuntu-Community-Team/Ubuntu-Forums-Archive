---
title: "&quot;The X system keyboard settings...&quot; How do I get rid of this error?"
date: 2007-11-21
forum: General Help
---

### Post by ticopelp on 2007-11-21
"The X system keyboard settings differ from your current GNOME keyboard settings." 

I get this error message after a fresh install of Gutsy, every time I reboot or log in. I have a separate /home/ partition with all my preferences and such intact, which may be where this is coming from, but I have no clue how to fix it. 

Please see attachment for the full message. Thanks in advance for any help.

---

### Post by tragicglee on 2007-11-22
That message drove me crazy for a week, and then stopped popping up, though I don't remember doing anything before or after :mad: 

Bit of a pain, but depending on the keyboard type you're using, I'd manually set whatever's got it wrong.  ( If you want GNOME settings, open /etc/X11/xorg.conf in your preferred editor with sudo/gksudo, change it and then save. If you want to keep the X settings, you'll find Keyboard type underSystem menu > Preferences Keyboard > Layout )

---

### Post by rune0077 on 2007-11-22
Oh man, I had that message too a while back. I think the real problem is, that what it says in you Xorg.conf file is not the same as what you have selected under System > Preferences > Keyboard. 

Try making sure the two settings are identical, and I think the problem goes away (key word here is *think*)

---

### Post by watsoncj on 2007-11-23
ticopelp,

I was able to get rid of this message by going to System > Preferences > Keyboard. Then choosing the Layouts tab. I clicked the default radio button and then clicked the 'Reset to Defaults' button. Probably an extra step in there but that did the trick for me.

---

### Post by ticopelp on 2007-11-23
Thanks very much! I'll try those out and see if any of them help.

---

### Post by loonicks on 2007-11-26
> **watsoncj said:**
> ticopelp,

I was able to get rid of this message by going to System > Preferences > Keyboard. Then choosing the Layouts tab. I clicked the default radio button and then clicked the 'Reset to Defaults' button. Probably an extra step in there but that did the trick for me.

For the record, this worked for me as well. I wonder why it happened. I did recently install the vncserver package, maybe that did it.

---

### Post by blaxnux on 2008-03-26
I also had that after uninstalling Xgl. I just simply go to system -> preferences -> keyboard, and then on layouts tab, pressing reset to default (even I am using the default options), and, whoooossss... It is gone. :D

---

