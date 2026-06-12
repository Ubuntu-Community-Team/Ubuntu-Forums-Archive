---
title: "How to run several programs at once in terminal"
date: 2007-06-15
forum: General Help
---

### Post by duncan.hawthorne on 2007-06-15
i want 2 programs to run at the same time, or quite soon after one another
not 1 program to run and finish, then the other, ie what would happen with gedit && eog
i want this to happen to put as a simple script file.
thanks for the help

---

### Post by Gwasanaethau on 2007-06-15
I think if you add '&' to the end of a command, it causes the command to run in the background allowing you to start another one, e.g. if you wanted to run gedit and then immediately run mplayer while gedit is still open, you could try:

```
$ gedit <somefile> &
$ mplayer <some media file>
```

Thus gedit will start, but you will be given a new prompt in the terminal to start the 'mplayer' command. I could be mistaken there, though.

---

### Post by Secession on 2007-06-15
What if you scheduled them to run with AT?  Although I would have to admit to not knowing the details, I'm imagining a script that gets the time then sets two tasks to run in a few seconds.  Can you do that in a script?  I'm a bit of a linux noob.

---

### Post by Gwasanaethau on 2007-06-15
> **Secession said:**
> What if you scheduled them to run with AT?  Although I would have to admit to not knowing the details, I'm imagining a script that gets the time then sets two tasks to run in a few seconds.  Can you do that in a script?  I'm a bit of a linux noob.

I'm not entirely sure I understand what you mean…do you mean that you want two tasks to run simultaneously at a certain time in the future?

I guess one way to do it would be to put the commands for the two tasks into a new text file in a format similar to that above and then use the 'at' command to schedule the time when you want them to start. I've never been able to get 'at' to run myself, I just can't get my head around the syntax for it, but in theory it should work.

---

### Post by Secession on 2007-06-15
That sounds like what I was aiming at.  As I say, I'm something of a Linux noob.  The principle seems sound though.

---

### Post by nymphaeles on 2007-06-15
Open a new console or use &.

---

### Post by duncan.hawthorne on 2007-06-15
& works perfectly, 
thanks loads

---

