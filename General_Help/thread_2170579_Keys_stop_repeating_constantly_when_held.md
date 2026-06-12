---
title: "Keys stop repeating constantly when held"
date: 2013-08-26
forum: General Help
---

### Post by aperezhrd on 2013-08-26
I'm having a problem that is driving me crazy since a week or two and I can't find a solution. When I am writing keys stop repeating while held, like when I want to go down with the arrow keys to move the cursor or to delete with the backspace. It always happens when I have 2 or 3 applications open (like Eclipse while writing code, chrome and may be the android emulator) and there is something making the CPU to work beyond the 20 or 30% of use. 

I've checked the syslog with tail -f /var/log/syslog and I've found that always that keys stop repeating, a message is written to the log that says:
```
keyboard: can't emulate rawmode for keycode 240
```
And is repeated all along the log. It stops appearing when I close most of the applications and I wait a few minutes. Because that's another thing, I'm not pressing any key when those messages appear, although keycode 240 seems to mean unknown key from what I've read it can be something different from a keypress I don't really know. 

I have an USB keyboard that I use, a cherry g80 with no special keys, pretty standard. I've unplug it and replug it again with no luck)

Here is some data:
Laptop ASUS k52f
Ubuntu 12.04.2 (kernel 3.2.0-49-generic and kernel 3.2.0-52-generic tested with no luck)
Gnome 3 (gnome-session --version tells is 3.2.1)

Does someone know what is going wrong?

Thanks!

---

### Post by aperezhrd on 2013-08-27
Still happening. I don't understand why it happens when I'm making use of the CPU. I've written and executed an infinite loop in bash to see if it triggers this bad behaviour and it does almost instantly. But why?

---

