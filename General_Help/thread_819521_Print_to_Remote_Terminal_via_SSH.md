---
title: "Print to Remote Terminal via SSH"
date: 2008-06-05
forum: General Help
---

### Post by blazercist on 2008-06-05
Hey guys this may seem odd but I want play a little prank on my wife...

I want to use SSH to open a gnome-terminal on my Desktop at home and print stuff to the terminal to make it appear as if the computer is talking to her.

Is it possible to SSH into my desktop at home and run gnome-terminal and print text on the screen there?  how would I do it?

---

### Post by HalPomeranz on 2008-06-06
SSH to your home machine.  Once there, issue the following commands:

```

$ sudo cp /var/lib/gdm/:0.Xauth $HOME/.Xauthority
[sudo] password for testuser: 
$ sudo chown testuser .Xauthority
$ export DISPLAY=:0
$ xterm &

```

This will cause an X terminal window to pop up on the system console.  Note that I'm using the username "testuser" in the above example, but you would obviously use your own username in the chown command above.

As for writing to the terminal, the first step is to track down the pty associated with your xterm process:

```

$ who
hal      tty7         2008-06-05 17:36 (:0)
hal      pts/0        2008-06-05 17:36 (:0.0)
hal      pts/1        2008-06-05 17:38 (:0.0)
hal      pts/2        2008-06-05 17:38 (:0.0)
testuser pts/4        2008-06-05 22:01 (:0.0)
testuser pts/5        2008-06-05 22:04 (some.host.com)

```

The xterm's pty is the one owned by testuser with the "(:0.0)" at the end of the line-- so pts/4 in the above example.  To write messages to this terminal, simply do something like "echo Hey baby... come here often? >/dev/pts/4".

You must promise to use this knowledge only for good, and not for evil...

---

