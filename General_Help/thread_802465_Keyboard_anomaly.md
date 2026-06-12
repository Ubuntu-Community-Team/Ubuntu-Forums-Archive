---
title: "Keyboard anomaly"
date: 2008-05-21
forum: General Help
---

### Post by Caribouhilltop on 2008-05-21
I just installed Ubuntu 8.04 on an Acer Travelmate laptop.

For some reason my "@" key produces a " symbol no matter what setting I try to use.

This makes it impossible to send e-mail.

Does anyone have any ideas?

---

### Post by cdtech on 2008-05-21
Some keys just work, because they are hardwired. I have the same FN key and all of mine execute (do what their labeled to do).

Some FN+fkey's or others do nothing or something other than what their entended and will let you know with an error in a log file, such as :

--------------------------------------------------
kernel: atkbd.c: Unknown key pressed (translated set 2, code 0xf4 on isa0060/serio0).
kernel: atkbd.c: Use 'setkeycodes e074 <keycode>' to make it known
--------------------------------------------------

These are the scancodes (e074). You can view this file while you press the unresponsive key combination to see if the kernel does see the combination. In a terminal type :

tail -n 0 -f /var/log/messages

xev ('X Events').
When you start xev from a terminal a small window will open, and your console fills up with output. You need this output.

If you use xev and see nothing from the combination that could mean that there are no keycodes associated with that combination. Just check the log file. The code you see from xev (in the terminal) are the keycode.

Some undefined keycodes in the input.h file are ; 84, 120, 195-199, 237-239

The keycode to attach to scancode can be found in that file at: /usr/include/linux/input.h

The command to set: `setkeycodes <scancode> <keycode>`

Hope this helps.....

---

