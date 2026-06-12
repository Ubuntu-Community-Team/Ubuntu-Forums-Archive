---
title: "Can't end Amarok process"
date: 2007-06-27
forum: General Help
---

### Post by dansued on 2007-06-27
I was running amarok with my ipod plugged in, tried ejecting it from inside amarok, didn't work and amarok froze. Had to do a sudo umount -l to get it unmounted.

The problem is that now amarok is completely frozen, system monitor shows a amarokapp process. I tried killing it and ending it, but it doesn't go away. It just sits there with a zombie status. This is preventing me from restarting amarok. Ctrl-Alt-backspace didn't do anything.

Please help!

---

### Post by Ayuthia on 2007-06-27
Did you try to do a sudo kill -9?

---

### Post by dansued on 2007-06-27
just tried it, same thing, didn't work.

Should I just restart ubuntu? I wanted to see how long of an uptime I could get, but I guess it's not important.

---

### Post by s_h_a_d_o_w_s on 2007-06-27
Alt+F2 And type "xkill" and press enter

click on Amarok

:D

---

### Post by s_h_a_d_o_w_s on 2007-06-27
then after you can run from Terminal and it will spit out any errors

---

### Post by dansued on 2007-06-27
ok so I just restarted the system, that got rid of it.

I think the error may be linked to a post-disconnect command that amarok preforms after you disconnect the ipod.

thanks guys

Edit: that only sort of fixed the symptom and not the problem. It happened again while transfering a song over to the ipod. I don't want to have to restart every time it freezes.

the xkill closed the window but it's still in zombie mode. running it from terminal just hangs, there's no error output.

---

### Post by Qu4k3R on 2007-06-28
If you got any more problems with amarok, I think that if you do a:

> 
sudo killall -9 amarok


This should kill amarok

---

