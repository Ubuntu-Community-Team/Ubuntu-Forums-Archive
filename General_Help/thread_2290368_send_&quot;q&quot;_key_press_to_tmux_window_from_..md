---
title: "send &quot;q&quot; key press to tmux window from .sh script"
date: 2015-08-11
forum: General Help
---

### Post by matthew_smith2 on 2015-08-11
I am pretty new to Ubuntu and am trying to use it on a EC2 instance.  I have been at it for a couple of weeks and I am learning my way around(slowly).

I have run into a problem with properly shutting down a program that I have starting at boot in a tmux window.  The instance gets a termination notice that I have a .sh running to look out for and it runs some commands when it happens.  I was just running the "kill" command on the window from the .sh on termination, but that loses the work that was done.

I am trying to put something in the .sh that will send the key press "q" to three different tmux windows to shutdown the program properly.  I have read up on tmux cheat sheets and .sh guides but I can't seem to find how to do it.

Can anyone help me?  Thank you.

---

### Post by Lars Noodén on 2015-08-11
If your tmux session is number 0, that is the only tmux session, you can do something like this to get 'q' in all three windows 0 through 2:

```

tmux send-keys -t 0:0.0 'q'
tmux send-keys -t 0:1.0 'q'
tmux send-keys -t 0:2.0 'q'

```

The -t option has the format session:window.pane.  The pane can be left off if you are not using more than one.  So can the session. e.g. -t :1 to get window #1 in session #0

---

### Post by Lars Noodén on 2015-08-13
You can also use names instead of numbers if you have named either the session or window.

---

