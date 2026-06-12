---
title: "I never thought i would be so helpless with Edgy !"
date: 2007-02-18
forum: General Help
---

### Post by akshaysrinivasan on 2007-02-18
I am writing in disgust for not getting a single answer to my question posted earlier.The XOrg keybindings have stopped working ,i cannot switch to a terminal ,i cannot stop gdm,i cannot kill Xorg with just ctrl+alt+backspace ,i don't even know if this is a bug ,i don't know if anyone has the same problem,i cannot find an answer on google ,for the first time i fell as if i was back to Windows ,i am left without an answer!

---

### Post by akshaysrinivasan on 2007-02-18
I finally found the problem.Ubuntu adds an entry like so in the Xorg .conf

Option		"XkbOptions"	"lv3:ralt_switch"

This disables Xorg from apparently listening to the keystrokes ,removing the entry removes the problem.

---

### Post by mcduck on 2007-02-18
> **akshaysrinivasan said:**
> I finally found the problem.Ubuntu adds an entry like so in the Xorg .conf

Option		"XkbOptions"	"lv3:ralt_switch"

This disables Xorg from apparently listening to the keystrokes ,removing the entry removes the problem.
..or you could just have used the left alt key instead :D

(on the finnish keyboard there is only the left alt key, the right one is Alt Gr that allows you to input huge amount of special characters from keyboard, that option in xorg.conf does the same thing)

---

### Post by akshaysrinivasan on 2007-02-18
I had no idea about that ,i wish someone had told me that earlier!

---

