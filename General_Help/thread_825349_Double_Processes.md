---
title: "Double Processes?"
date: 2008-06-10
forum: General Help
---

### Post by anotherdisciple on 2008-06-10
I have 2 of each of these processes at startup:

[LIST]
[*]dbus-daemon
[*]gdm
[*]pdflush
[*]Xorg
[*](3) of sh
[*](5) of getty
[/LIST]

Sometimes there are 2 of the trashapplet and all the processes that start with gvfs... But I only notice it when my wife logs in and then I log in. So that must be a multi-user bug.

This all adds up to more RAM being used that I expect out of a linux system. My computer isn't slow at all... I just wanted to tweak it the best I can.

Also, I use around 20% of my CPU at idle... back in my Windows days I used to use about 2-4%. How can I tweak this to improve performance and reduce the heat of the CPU? I use GKrellm, but that fan turns on high an awful lot! Xorg uses 5-15% at idle... some of the % is just running the gnome system monitor... about 3%. Compiz uses a little too... even at idle... but I expect a little CPU usage for eye-candy.

---

### Post by HalPomeranz on 2008-06-11
It's normal to see multiples of all of the processes you list, EXCEPT for the Xorg process which I'm not entirely certain about.  Can you post the "ps -ef | grep Xorg" output so I can figure out what these processes are?

---

### Post by anotherdisciple on 2008-06-11
```
nick@laptop:~$ ps -ef | grep Xorg
nick      8710  8683  0 23:40 pts/0    00:00:00 grep Xorg
```


Hmmm... I'm not sure how to interpret that...

---

### Post by molotov00 on 2008-06-11
That's saying there are no Xorg processes running. Linux is case sensitive though; try xorg?

If you run 'ps -ef' then you'll see what's happening more clearly. It's just a list of processes.| (that's a pipe) sends the output of the command to 'grep'. grep Xorg is just saying "only show me the lines that have Xorg somewhere in it".

In your code, there aren't any processes running called Xorg. The command only returned the command you'd just run.

---

