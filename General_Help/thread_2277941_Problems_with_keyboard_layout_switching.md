---
title: "Problems with keyboard layout switching"
date: 2015-05-12
forum: General Help
---

### Post by iscott2 on 2015-05-12
Since upgrading to Ubuntu Gnome 15.04 my layout switching seems to be confused and partially broken. 

I have the following shortcuts set under settings>keyboard>shortcuts>typing:

[LIST]
[*]"Switch to next input source" is <super><space>
[*]"Modifiers-only switch to next source" is <shift><caps lock>
[/LIST]

**First**, these two shortcuts seem to be using two different layout-switching methods:


[LIST=1]
[*]**<super><space>** **brings up a modal interface** with all of the configured keyboards. If I hold <super> and tap <space> I can cycle through those methods. The language indicator in the top panel switches accurately.
[*]**<shift><capslock>** does not bring up the modal switching interface, but **switches the top panel language indicator**.
[/LIST]

So my first problem is that I don't understand why the two shortcuts do different things.

**Second**, the <shift><caps lock> shortcut doesn't work properly.


[LIST]
[*]When using this method the **language indicator is out of sync** with the actual active keyboard. The active keyboard is one position "ahead" of the one given in the keyboard indicator.
[*]My **Hebrew keyboard** (which I can use find with the <super><space> method) **can't be activated** using <shift><caps lock>. That position in the cycle of layouts seems to activate my regular en_us keyboard.
[/LIST]

I don't know whether this has anything to do with the fact that I have five keyboards configured: en (us), en (international), gr (polytonic), he (biblical, Tiro), am (Amharic). In the past there was a hard limit in Gnome that would not allow more than four layouts to be configured. At some point recently that limit seems to have been lifted, and I was able to work with 5 configured layouts for the past six months or so.

Any help is much appreciated!

---

