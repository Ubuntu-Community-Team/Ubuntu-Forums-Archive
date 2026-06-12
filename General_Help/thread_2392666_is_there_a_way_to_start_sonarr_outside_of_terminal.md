---
title: "is there a way to start sonarr outside of terminal?"
date: 2018-05-23
forum: General Help
---

### Post by jgw on 2018-05-23
I am using 18.04    I am wondering if its possible to launch sonarr (or any oither program) without using the terminal.  The problem is that when the terminal is used one cannot turn it off without turning off the program too.  It used to be, in 16.04 that one could do an alt a and then put in such a command.  That seems to be no longer possible.  My starting command, for sonarr is:
mono --debug /opt/nzbdrone/nzbdrone.exe

I also suspect that a category for questions about 18.04 might be in order until the changes are dealt with as there seems to be a lot of them.

Thank you....................

---

### Post by deadflowr on 2018-05-23
alt + F2?
or create a desktop launcher

---

### Post by jgw on 2018-05-23
Thanks for the reply AND the answer!!!

I will mark this one solved

---

### Post by deadflowr on 2018-05-23
You can also utilize the history of the alt +F2 run dialog by using the up/down keys to scroll through the commands you've used in the past.
That should save time by not having to type the command every time.
This applies to Ubuntu's default desktop gnome shell.

If you still use unity, then that has a more gui-rich method, like unity does.
Where by simply opening the run dialog you'll instantly (or mostly instantly) see the recently used commands, and all you need to do is select one to run
(unity's allow either a mouse click or arrow keys)
fwiw

---

### Post by jgw on 2018-05-23
Thanks again!

I will get it - just takes time on new stuff <G>

---

### Post by tledford on 2018-05-23
> **jgw said:**
> I am using 18.04    I am wondering if its possible to launch sonarr (or any oither program) without using the terminal.  The problem is that when the terminal is used one cannot turn it off without turning off the program too.  It used to be, in 16.04 that one could do an alt a and then put in such a command.  That seems to be no longer possible.  My starting command, for sonarr is:
mono --debug /opt/nzbdrone/nzbdrone.exe

I also suspect that a category for questions about 18.04 might be in order until the changes are dealt with as there seems to be a lot of them.

Thank you....................

I know this is marked [SOLVED] and it is tangential to what you're asking, but I wanted to point out (in case it is useful to you in the future) that to launch a program from the terminal and have it continue to execute when you close the terminal, just append an ampersand, as in:

mono --debug /opt/nzbdron/nzbdrone.exe &

---

### Post by jgw on 2018-05-24
Thanks for the thought.

I knew about that one but it didn't seem to work on one I tried and so I asked the question - and got the answer!

Thanks again!

---

