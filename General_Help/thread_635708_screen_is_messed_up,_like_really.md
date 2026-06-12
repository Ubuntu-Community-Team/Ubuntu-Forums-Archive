---
title: "screen is messed up, like really"
date: 2007-12-09
forum: General Help
---

### Post by simplekin on 2007-12-09
Alright, so i was trying to add on extra buttons for my MX510 mouse, then i pressed CTRL ALT BACKSPACE, and instead of restarting the session, it just kept coming back to the screen i had, but it was horribly rendered, and i couldnt do anything, even move my mouse,   then when i restarted, the screen was so jumbled up that i cant see anything
like there are lines, and original colours, but it looks like every pixel is out of place. So here are my questions:


How can i enter reduced graphics mode
How in general do i fix it? the way im talking to you know is i just popped in the instalation CD

---

### Post by mali2297 on 2007-12-09
There might be easier ways, but..

Press Ctrl-Alt-F1 to come to a virtual terminal, then type
```

sudo dpkg-reconfigure xserver-xorg

```
You will be asked a bunch of questions, answer them as best you can. If you are uncertain, just choose the default and press Enter.

After this, press Ctrl-Alt-F7 to come back to your desktop and then Ctrl-Alt-Backspace to restart the X session.

---

