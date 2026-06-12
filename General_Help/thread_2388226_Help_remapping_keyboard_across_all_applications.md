---
title: "Help remapping keyboard across all applications"
date: 2018-03-30
forum: General Help
---

### Post by lordwillin on 2018-03-30
Hello good people.  I inherited a Lenovo Thinkpad that is now running Ubuntu 17.10.  One reason why I got this laptop for free is because there is some kind of short in the Backspace key.  The keyboard doesn't give you a backspace when you want it, it saves them up and unleashes them in huge disruptive bursts.

I am trying to disable Backspace and remap the 'backslash, vertical bar' key to Backspace.  I've been reading manuals and forum posts for a couple of hours and I'm still not getting it.

I've been able to execute

```
xmodmap -e 'keycode 22 = 0xFFFFFF'
# turns off backspace
xmodmap -e 'keycode 51 = 0xFF08'
# makes \ into backspace
```

from the terminal, which only seems to affect typing in the web browser (like right now) and a few other places, but in the terminal itself, and in LibreOffice and other places where I need it, the old keymap remains.   

I believe that my answer might lie in "XTerm*ttymodes"   but I can't find the documentation that will make that work for me.  All the docs I have read are about how to exchange DEL for BACKSPACE, but they don't tell me how to work with the Backslash key that I'm trying to get to generate a backspace.

Thanks in advance.

---

### Post by TheFu on 2018-03-30
For many laptops, replacing a keyboard is about 3 minutes and $20.  Just sayin'.

Of course, there are some chromebooks where replacing a keyboard is $120 and an hour because the entire machine has to be taken apart to get from the battery, to the motherboard to the touchpad-keyboard assembly.

17.10 changed many things related to X11. I'm not certain what will and won't work, but Wayland is the default display manager, not X11. Don't know if this matters or not.

---

### Post by lordwillin on 2018-03-30
Yeah, I thought of replacing the keyboard, but it seems like it would set me back $40 or $50, which isn't out of the question, but until that happens (if it does) I'd like to have a workaround.

---

### Post by TheFu on 2018-03-30
> **lordwillin said:**
> Yeah, I thought of replacing the keyboard, but it seems like it would set me back $40 or $50, which isn't out of the question, but until that happens (if it does) I'd like to have a workaround.

I'm using the WM features, openbox, to control this stuff. Won't work for anything that isn't openbox, so probably not useful to you. Plus, I'm not on 17.10 and have avoided wayland due to my personal requirements.

I feel it too. Left-arrow key is broke here ... and I'm on a chromebook. That means there aren't any extra keys to reuse and I've already used most chords.

---

