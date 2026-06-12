---
title: "all tty's appear as a pinstriped screen. X ok though.."
date: 2005-10-04
forum: General Help
---

### Post by fourchannel on 2005-10-04
I'm not entirely sure how it happened. but all my virtual consoles are messed up. they were fine on boot, no problems using them when i first brought the computer up.

 All of them are completely illegible, and have pinstripes (vertically, about 100 or so) covering the whole screen. you can see where the cursor is, but no text shows up. I tried the reset command, but all that does is just move the cursor to the top of the screen. you still can't read anything.

X and all the pts's are working fine though....

If I send stuff to the tty, it responds to it. e.g.

```
# ps aux > /dev/tty1
``` causes the cursor to move positions, but no text.

So, can I force a tty to reset? is there a command for that?

I could reboot, and that would probably fix it, but i'm curious if this problem can be fixed without restarting the computer.

---

### Post by tktreload on 2005-10-04
the only time i saw anything that looks like what you describe is when i tried to clone the X session (dual screen on tv out) on my nvidia card. I got small green stripes and spots in my tty, but only when the tv was connected, when it was not the cloned screen was "next" to the real one...strange things happen...

---

### Post by fourchannel on 2005-10-05
i have just discovered the awesomeness of hibernate. now i have so many random webpages loaded if i do a reboot i'll never find the stuff again. now i have to find a way to force it to fix lol.

that or spend an hour making bookmarks.

---

