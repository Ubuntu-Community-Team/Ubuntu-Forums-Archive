---
title: "Thunderbird pegging the CPU meter"
date: 2013-01-06
forum: General Help
---

### Post by Rocket J Squirrel on 2013-01-06
Lubuntu 12.04, Thunderbird 17.0

Started about a week or so ago. Thunderbird pegs the cpu meter in htop and Task Manager. The pegging can last a few seconds, to several dozen seconds or a few minutes. I've had to resort to killing the process more than once just to get the system to respond. This with TB running normally or in Safe Mode. 

Anyone else experiencing this?

---

### Post by conradin on 2013-01-06
Lots of ppl having this trouble:
But have a look here:
[http://forums.mozillazine.org/viewtopic.php?f=31&t=1986503](http://forums.mozillazine.org/viewtopic.php?f=31&t=1986503)

---

### Post by Rocket J Squirrel on 2013-01-07
Thanks, Conradin.

I searched the web for info about this issue and already tried the suggestions described in the link you helpfully provided, with the exception of deleting all the .msf files, which I just now tried but that didn't fix it.

The issue here seems to occur mainly when composing an email. Backspacing over a word to write another, or misspelling a word will often cause the program to freeze, and peg the cpu-meter. The freeze may last for a short while, or it might go on and on. 

It may be related to the spell-checker, because it would often pause -- sometimes for quite a while -- while trying to digest a misspelling, so I turned off online spell checking and that fixed the problem for several months, maybe up to a year. But now I have this problem even with spell-check turned off.

And other times it seems to freeze on its own, with high cpu usage.

If I'm the only one having this issue then it's something wonky on this machine.

---

### Post by Rocket J Squirrel on 2013-01-08
PARTIALLY SOLVED.

Turns out that it was two gmail IMAP accounts that were bogging down TB. Once has emails going back to 2007 -- tens of thousands of emails. By doing Edit >> Account Settings >> (select account) >> Synchronization & Storage and then unticking "Keep messages for this account on this computer", TB got unbogged. 

But TB's memory usage is still obscene. It's at 1.3GB of VM at the moment. That's another matter.

---

### Post by John.Klockenkemper on 2013-01-08
There is a direct correlation between size of the inbox and utilization. Once all mail has been downloaded, go back through and archive the email 1 month at a time. This should bring the utilization down to a normal level.

---

### Post by Rocket J Squirrel on 2013-01-08
I have a retention policy for the two IMAP inboxes to only keep the last 30 days' worth of email. So those aren't getting huge. 

But these are gmail IMAP accounts and Archiving doesn't do anything when I go into the Gmail subfolder of the account and attempt to archive the Inbox there. Maybe there's another way to go about this, a different way to set up the accounts so TB isn't shouldering the work, since everything is stored at gmail.com anyway.

---

