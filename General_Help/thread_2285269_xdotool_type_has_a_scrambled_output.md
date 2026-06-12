---
title: "xdotool type has a scrambled output"
date: 2015-07-04
forum: General Help
---

### Post by dev18 on 2015-07-04
Greetings,
    I have two questions. 

1) First, where do questions like this belong on this forum so I can find an accurate audience for help in the future.

2) I'm trying to learn how to use xdotool. I wrote a script which is somewhat like an irc bot. It was working fine yesterday, but not today. When using the xdotool to type a variable string, it becomes slightly scrambled. However. manually writing the command out in the terminal works.

Command: xdotool type "$message"

Original string ($message): "/w 1234 abcdefghijklmnopqrstuvwxyz"

xdotool output:134 iabcdefghklmoq2stvwjpyziruxn

After a reinstall: 124 kdefghkl qru3oyzacgjmotwbipsvxn
_____________
xdotool version 3.20140217.1
_______________
       Thank you,

---

### Post by dev18 on 2015-07-04
Update: I did a make install from the github repo and it works. Thanks for looking all those who tried to help.

---

