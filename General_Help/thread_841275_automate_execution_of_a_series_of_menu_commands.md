---
title: "automate execution of a series of menu commands"
date: 2008-06-26
forum: General Help
---

### Post by figgles on 2008-06-26
Is there a utility that allows the scripting of the execution of a series of menu commands? Some similiar utilities include QuicKeys for Mac and Windows, and I know that vbscript lets you access gui-controls programmatically.  For example, I'd like to automate the execution of thunderbird's file menu > offline > sync now functionality, as the autosync feature in thunderbird isn't as reliably as the gui-driven selection method. Even if I'm wrong in this specific example, can I drive the automation of a series of menu commands and dialog choices?

Thanks in advance!

---

### Post by ryanhaigh on 2008-06-26
I have never tried this but you could look at something like xmacro. You might also be able to do it by simulating key presses (assuming you can do this specific action this way). You would need to ensure that thunderbird has focus which could be done using wmctrl.

This script is not tested as Im not on my ubuntu machine, it also assumes the key combination to sync but you can adjust that to what it really is.

```

wmctrl -a "thunderbird" #make sure thunderbird is active window
xte "key Alt_L"    #press alt
xte "key f" &&     #file
xte "key 0" &&     #offline
xte "key s" &&     #sync
exit

```

---

### Post by figgles on 2008-06-27
> **ryanhaigh said:**
> I have never tried this but you could look at something like xmacro. 
Thanks -- I'm checking it out now.

---

