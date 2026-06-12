---
title: "Shell script and telnet"
date: 2006-09-20
forum: General Help
---

### Post by Azurlune on 2006-09-20
Hi there,

I'm trying to get a shell script to work via crontab, and I'm having some problems. It exectutes fine if I do if from a terminal myself, but it doesn't finish running from cron. What it does is test my internet connection (by pinging the bbc) and then if it is down, run a script which restarts my router via telnet. The way I've done it is with three scripts, one which checks the net connection (this is the one in the crontab), then calls the second one if there is none. The second script pipes a third script, containing the commands, to telnet.  I tried combining scripts two and three but it didn't seem to work, so I seperated them.
I think the problem is to do with them not running from an interactive shell? But if I call them from sh -i, either at the start of the script or from the crontab, it doesn't seem to do anything.
This is my first real need to shell script, so I don't have much experience with it. Some help would be appreciated :D
Ta!

---

### Post by LotsOfPhil on 2006-09-20
Can you post the scripts, the entry in cron, and what you type in the terminal when it "works"?

---

### Post by Azurlune on 2006-09-20
Ah, I have it working now, case of, "try a little bit more before asking on the forums".

I just had to call script three via sh -i instead of calling it straight. But, working now, so I'm happy :D

---

