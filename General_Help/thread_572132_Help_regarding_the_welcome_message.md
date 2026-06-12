---
title: "Help regarding the welcome message"
date: 2007-10-10
forum: General Help
---

### Post by blackaardvark on 2007-10-10
Could someone be kind enough to give me a rough idea what I would need to read up on to figure out how to write some kind of script or something that can change my welcome message each time I start ubuntu? I'm thinking of having either a random quote each day or something like that.  

I wasn't sure where to put this query so I put it here.

Thanks.

---

### Post by yabbadabbadont on 2007-10-10
You could add something to /etc/rc.local to change the contents of /etc/motd.  This would happen at each boot.  If you leave your system up, then change motd from /etc/crontab.

---

### Post by erlingerle on 2007-10-10
Install "fortune" and put 
```

fortune > /etc/motd

```
in your crontab

---

### Post by melopsittacus on 2007-12-29
Hi! I would like to display fortune at startup, however not in the text terminal, but on the graphical one. To do this, I want to autorun a gnome terminal which then runs fortune and remains usable for other commands. 
I have tried with the following command:
```
gnome-terminal -x fortune
```
This opens the terminal and shows the quotation, however after that the terminal remains unusable for other commands. What do I have to do in order to continue using it?

---

### Post by yabbadabbadont on 2007-12-29
Try piping the output of fortune to xmessage instead.

```
fortune | xmessage -default okay -file - &
```

If you find that you can't get the command to run directly, try putting it into a shell script and then run the script instead.

---

### Post by melopsittacus on 2007-12-30
Thank you for the suggestion, this approach is better than my original one.
Unfortunately however it works only when I run it manually, but it does nothning when started automatically at startup, neither invoking the command directly, nor through a script.

My script is (it has also the running permission):
```

#!/bin/bash
fortune | xmessage -center -default okay -file - &

```
and when I run it manually, it works fine as mentioned.

I think the problem might be that the startup items do not run in the correct order, so perhaps the message gets displayed for a very short time, but then some other program kills it immediately. 

So does anybody know how can I set the order in which the startup items get started?

I saw that in the Sessions window, under "current session" tab there are some items which have a number meaning the order, but fortune is not listed there, and anyway some items have the same number. What decides the order between two items which have the same number?

---

