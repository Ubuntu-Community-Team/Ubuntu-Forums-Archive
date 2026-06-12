---
title: "Server suspend and resume"
date: 2019-01-16
forum: General Help
---

### Post by pln19 on 2019-01-16
Hi!
I am running Ubuntu server (18.04 LTS). I use it as an platform for music-streaming.
It is running 24/7 but that is unnecessary, so I want it to suspend in the late evening and then start again next day.
I have been googling and trying to figure out how this is done. 
My question is: how do I configure my Ubuntu to auto-suspend and auto-resume.
Observe. I have to do this in a terminal. I don´t use any graphical desktop. In fact I don´t use a monitor at all, I use ssh and another computer.

---

### Post by TheFu on 2019-01-16
**sudo pm-suspend** is the command, assuming everything necessary is setup and working.  I don't suspend my servers and only suspend a laptop, which has always "just worked."

I have no idea how to wake it, unless the BIOS has a wake feature built into it.

---

### Post by pln19 on 2019-01-16
The suspend command nowadays is to my knowledge [B]systemctl suspend. 
[/B]However, I want to configure auto-suspend (and resume)

---

### Post by CatKiller on 2019-01-16
Resume would have to be as an alarm in the BIOS (or wake-on-LAN) since the rest of the computer wouldn't be running.

---

