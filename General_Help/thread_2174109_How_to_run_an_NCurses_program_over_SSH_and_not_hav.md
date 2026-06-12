---
title: "How to run an NCurses program over SSH and not have it close when I exit?"
date: 2013-09-12
forum: General Help
---

### Post by RedArmy90 on 2013-09-12
Hello,

So I have a server running ubuntu and there is an NCurses program that I would like to be able to turn on and just run for a long time. The trick is that I have to do it over SSH and I know that if I start a program over SSH and then close the connection, it will stop running on the system itself. I also want to be able to come back to this program when I feel like it and log in. I was wondering if this is even possible to do.

Any help on this topic would be greatly appreciated. Thank you in advance.

---

### Post by HiImTye on 2013-09-12
you want to use either screen (older) or tmux (better). instead of exiting, detatch your session (hotkey, d) and it will continue to run when you disconnect. when you want to reconnect to it, use one of
```
tmux -attach
# --- or ---
screen -r <session name>
```
here's some more info for each

screen:
[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)
tmux:
[http://blog.hawkhost.com/2010/06/28/tmux-the-terminal-multiplexer/](http://blog.hawkhost.com/2010/06/28/tmux-the-terminal-multiplexer/)

---

### Post by Lars Noodén on 2013-09-13
+1 for screen or tmux

They will do what you want

I would also recommend tmux instead of screen if you are just starting out.

---

### Post by RedArmy90 on 2013-09-16
That helped a lot guys. I'm using tmux. Thanks a bunch!

---

