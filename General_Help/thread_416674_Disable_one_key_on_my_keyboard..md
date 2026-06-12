---
title: "Disable one key on my keyboard."
date: 2007-04-21
forum: General Help
---

### Post by paul la c on 2007-04-21
How can I disable on keyboard key from ever being registered by the OS? I ask because my backslash key is buggered and randomly firing all the time and making my computer unusable.

My current hack (which is working) is a bit of plastic jammed underneath Ctrl and left Shift, going over the backslash key to hold it down continuously so it gets ignored and doesn't interrupt my typing. It is the keyboard on my laptop which is why I don't simply by a new one.

---

### Post by 23meg on 2007-04-21
- Start a terminal and type "xev", press return
- A window will pop up; make sure it's focused, and press the key you want to disable
- Note the "keycode" value that appears in the terminal
- Close the xev window and type **xmodmap -e "keycode XX= 0x0000"**, where XX is your keycode

---

### Post by paul la c on 2007-04-21
Thanks, it didn't work but was worth a try. I think maybe some applications (Fx and Oo still get full of backslashes when the bit of plastic isn't in place) don't use the same keyboard map or something *doesn't really understand what he's talking about*

---

### Post by 23meg on 2007-04-21
It does work with some applications, but not with others?

---

### Post by paul la c on 2007-04-21
The only program that notices a difference is the event handler that I used to get the "keycode" (94, btw).

---

### Post by Techrocket9 on 2008-06-26
Thx. Ths has saved my lve. The only problem s that  need the (eye) key. s there a way to map the letter (eye) to another key? N0w the (0) key has g0n bad. (These are a zer0s). H0w d0 (eye) map that 0ne t00?

---

### Post by frith on 2008-07-12
seriously, this one made me laugh out loud.

I'm not sure if you meant it, but damn, that is funny!

All y0u n33d t0 d0 1s l3arn t0 sp33k l1k3 an aw3s0m3 haxx0r!!0ne0ne

Heh.

Okay, seriously, you just need to remap the keyboard. It can be pretty time consuming, but you can remap any key to any symbol really, using xmodmap.

Here is a little link I found by googling.

[http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html](http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html)

Give that a try...

(once again, hilarious :)

---

### Post by Techrocket9 on 2008-07-15
Thanks for the help, but I have a new keyboard now.

---

