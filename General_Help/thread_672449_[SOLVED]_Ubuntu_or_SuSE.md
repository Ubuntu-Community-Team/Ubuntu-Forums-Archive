---
title: "[SOLVED] Ubuntu or SuSE?"
date: 2008-01-19
forum: General Help
---

### Post by TomR55 on 2008-01-19
I have two elderly parents who like communicating with their family members via eMail and enjoy surfing the Internet, etc. Anyway, they have a Windoze box and are irritated by the constant Windoze issues, e.g., Virus updates, Phishing and other Ad(Mad)ware software, etc. 

So, I have one or two older PCs --perfectly reasonable machines, just smaller disks, etc. The question is not whether I'll build a Linux box for them but which Linux. I like SuSE because I know how to set it up so that no Login screen appears at boot; moreover, SuSE has Yast which is configurable to work unattended (not necessarily a good thing?). I'm thinking that they can use start-up, no Login required, read mail, etc., Shutdown and they are done is less time than it takes to boot Windoze.

Now, recently I've used Ubuntu --Feisty and Gutsy-- and two different machines and am favorably impressed. I guess it boils down to these questions (unless the forum can think of others):

1) Can Ubuntu be set-up so that a default user is logged on at start-up?
2) Can Software Updates be automated, or is this even a good idea?

Naturally, if I've overlooked anything, I'm sure than many kind and patient members of this Forum will point these out.

Thanks in advance for any input or advice.

TomR

---

### Post by rfruth on 2008-01-19
yes to auto login no (that I know of) to all auto update

---

### Post by melopsittacus on 2008-01-19
Hello! I don't know about the automatic login, but the updates of the packages occour almost automatically: a little icon notifies you that there are updates, and if you click on it you get the update manager which lists them, and if you click download and install, everything happens without you having to do anything else.

---

### Post by dan0z on 2008-01-19
Hi,

I am fairly new to Ubuntu myself but can answer question 1 :D

Yes you can have a user login automatically, and luckily its fairly easy to do:

Goto: System > Administration > Login Window

Then click the "Security" tab, and there is an option for "Automatic Logon"

Dan

---

### Post by heindsight on 2008-01-19
It is possible to automatically configure Ubuntu to automatically install security updates without asking for confirmation. I'm not sure whether this is really a good idea. I would have said that I don't think it's a bad idea, but after the xorg update snafu this week, I'm not so sure anymore. 

It is also possible to completely disable updates. Again, I'm not sure it's a good idea, but if you have the system up with everything working the way you want it and you're careful to avoid dodgy websites or opening email attachments from untrusted sources, then disabling updates shouldn't be a problem.

EDIT:
I forgot to say, having used both SuSE and Ubuntu, I'd say that Ubuntu would probably be easier for novices.

---

### Post by melopsittacus on 2008-01-20
> **heindsight said:**
> It is possible to automatically configure Ubuntu to automatically install security updates without asking for confirmation. I'm not sure whether this is really a good idea. I would have said that I don't think it's a bad idea, but after the xorg update snafu this week, I'm not so sure anymore. 


Well, does it make any difference if it is installed automatically or you have to confirm it? I do not think there is a way of checking if the update is all right before you install it, even if you have to confirm...

---

### Post by heindsight on 2008-01-20
> **melopsittacus said:**
> Well, does it make any difference if it is installed automatically or you have to confirm it? I do not think there is a way of checking if the update is all right before you install it, even if you have to confirm...

Well, if an automatically installed update breaks things, it can be quite difficult to figure out the cause of the problems. One moment everything works, then an update automatically installs itself without you knowing about it and the next moment things aren't working anymore. At least if you had to confirm the update first, you would know that it was the update that caused the problems. Also, having to confirm the update first, gives you a chance to say, check the forums to see if anyone else has had any problems with it.

---

### Post by melopsittacus on 2008-01-20
You are right, Heindsight, I did not think of that :)

---

### Post by forestpixie on 2008-01-20
I tend to wait a day anyway after I got caught with a kernel update problem when gutsy was new - then once there are a few 'it's been fixed now' threads I update it

---

### Post by mr.farenheit on 2008-01-20
which one are you more comfortable fixing is a question because most likely when something does go wrong they will come to you for answers.

---

### Post by TomR55 on 2008-01-20
Excellent point! I'm thinking about a recent complication with Feisty and Xorg .. If I hadn't interacted with the updater I wouldn't have understood what was going on ... or, worse.

Thanks for your insight. I will just have to instruct them in how to run the Update Manager, which is no big deal, really.

TomR

---

