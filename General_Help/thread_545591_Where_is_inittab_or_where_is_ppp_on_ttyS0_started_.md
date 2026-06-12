---
title: "Where is inittab or where is ppp on ttyS0 started from??"
date: 2007-09-07
forum: General Help
---

### Post by MrUmunhum on 2007-09-07
Hi guys,

  I installed Ubuntu 7.04 and I am getting full logs with complaints about IRO on ttyS0.

 Doing a 'ps axw', I see that there is a ppp session on ttyS0.  Killing that process will stop the errors from logging.

  I don't know where to stop this process from starting?  There is not 'inittab' and there is nothing in '/etc/events.d' that references ppp or ttyS0. 

  Where does this ppp session get started from and how do I stop it from starting?

  Thanks for your time.

---

### Post by banewman on 2007-09-07
There is a man page for ttys - but it only goes to 3. Still looking. :) man ttys tells how to create it not change it
Googleing ttys0 gives responses that are mostly errors/can't find - are you on dialup or did you configure the network manager for dialup?
Try looking in /dev/ttys0 - lol

---

### Post by geraldm on 2007-09-07
Chances are good that you would find ttyS0 mentioned in one of the scripts under the directories in /etc/ppp .  One of the starting programs might be mentioned in the 
scripts in /etc/init.d/*.  

Type the command ( to see what run level you are at )
runlevel
Then use that number to replace X in /etc/rcX.d/
That is the directory that has links to Start or Kill the scripts in /etc/init.d/*

Gerald

---

