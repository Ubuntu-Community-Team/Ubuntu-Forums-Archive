---
title: "blank screen on start x"
date: 2006-11-21
forum: General Help
---

### Post by milton1 on 2006-11-21
I apologize for what may seem like a redundant post, and I realize that there are many, many similar questions on the board already, but I don't see exactly my symptoms on any of them, so I am adding one more.

My system boots fine and gets as far as starting x, when it will hang at a blank screen the first time I boot it in the morning. If I then shut it down by holding the power button and boot it again, it boots fine.

I have disabled usplash after fighting with that problem for a while, and I have disabled all network settings other than the one that I am using.

Any suggestions?

---

### Post by Jimmey on 2006-11-21
When it hangs, try pressing CTRL + ALT + F8(Maybe F7 - I can't remember). It might show some error messages there.

Also, when it does hang, try going to another TTY using the method I described (CTRL + ALT + F1-11), and logging in. Then try "sudo /etc/init.d/gdm restart". See if that does anything *-)

---

### Post by milton1 on 2006-11-21
Thanks for your suggestion, but I've tried that. I seem to get no response from the keyboard. It is very odd. On the second boot it always works fine.

BTW, running kubuntu.

---

### Post by milton1 on 2006-11-21
Just to add one more piece of info: Before I disabled usplash, I was dealing with the popular bug of having only a blinking cursor at boot and having the boot process take forever. It was painfully slow, but it booted every time... eventually. Now it boots fast, but I have to boot it twice. (still faster than waiting with the usplash problem)

---

### Post by wongdai on 2006-11-21
Yep, I have EXACTLY the same problem.  I have no idea how to fix it however.

---

### Post by milton1 on 2006-11-21
More info on the system (in case it helps):

Gateway E-series
P4 2.4 GHz
256 MB RAM
Intel 82845 G/GL onboard graphics
driver = i810

---

