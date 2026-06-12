---
title: "Linux Security."
date: 2006-08-11
forum: General Help
---

### Post by Roasted on 2006-08-11
I was just wondering, is Linux secure right out of the box? Or is there some kind of tweaking you can do to Linux to make it more secure and less vulnerable to intruders and hacking and other things of that nature?

---

### Post by bjweeks on 2006-08-11
It's secure enough for you.

---

### Post by Roasted on 2006-08-11
Yeah I know that much, but I'm just trying to get an understanding of how customizable it can be security wise. That's all I'm asking. Like with Windows, you download additional service packs and keep up to date on things to maintain a secure system. Is that all you do here on Linux?

---

### Post by bjweeks on 2006-08-11
> **Roasted said:**
> Yeah I know that much, but I'm just trying to get an understanding of how customizable it can be security wise. That's all I'm asking. Like with Windows, you download additional service packs and keep up to date on things to maintain a secure system. Is that all you do here on Linux?

Yes, just keep it updated.

---

### Post by FenrisAbraxas on 2006-08-11
> **Roasted said:**
> Yeah I know that much, but I'm just trying to get an understanding of how customizable it can be security wise. That's all I'm asking. Like with Windows, you download additional service packs and keep up to date on things to maintain a secure system. Is that all you do here on Linux?

Every default installation is unsecure mainly because every system will installed is pretty much vulnerable to known bugs and security errors.

It's recommended that you upgrade inmediatly and install a firewall (if you connect directly to the internet, if you are behind a router it's not the top priority).

---

### Post by bjweeks on 2006-08-11
> **FenrisAbraxas said:**
> Every default installation is unsecure mainly because every system will installed is pretty much vulnerable to known bugs and security errors.

It's recommended that you upgrade inmediatly and install a firewall (if you connect directly to the internet, if you are behind a router it's not the top priority).

Ubuntu doesn't need a firewall because it has no running daemons.

---

### Post by Jagot on 2006-08-11
Ubuntu already comes with a firewall in the form of IPtables, so packages like Firestarter are just there for you to configure it more.  All ports are closed in a default Ubuntu installation.  As FenrisAbraxas says - do all the updates.

---

### Post by Roasted on 2006-08-11
I just spoke to a dude who swore to me the Windows shell was more secure than Linux. I didn't even know how to respond, so I just flat out stopped responding to him. I have never once heard someone say that to me. Not any of my professors, not any of the programmers at work, not even my relatives who work at the pentagon. I just figured I'd post to see what some other folks thought.

---

### Post by bjweeks on 2006-08-11
> **Jagot said:**
> Ubuntu already comes with a firewall in the form of IPtables, so packages like Firestarter are just there for you to configure it more.  All ports are closed in a default Ubuntu installation.  As FenrisAbraxas says - do all the updates.

Ubuntu doesn't "close" any ports.

---

### Post by bjweeks on 2006-08-11
> **Roasted said:**
> I just spoke to a dude who swore to me the Windows shell was more secure than Linux. I didn't even know how to respond, so I just flat out stopped responding to him. I have never once heard someone say that to me. Not any of my professors, not any of the programmers at work, not even my relatives who work at the pentagon. I just figured I'd post to see what some other folks thought.


Well you can't say Linux is more secure as a fact, but put it this way. Put an idiot at a Windows box and Linux box, the Windows box will get owned first.

---

### Post by red_shrike on 2006-08-12
It is true that Linux is more secure out of the box than windows. Use firestarter and do updates if you have fast enough internet connection. On the other hand, amount of security updates on windows and linux shows that there are fewer on win. Does that mean Linux is less secure? Maybe. Depends. Most of the security hazards are comming from programs involving professional tools or services and programs not commonly used by desktop users. Even at that, fixes are issued faster on lin than on win. On the other side again, Lunux/UNIX user security policies and user management is by far better than in windows. There are very few hard to obtain viruses, and no malware. All and all, desktop linux users are by far more secure than windows ones. Just don't use root account.

---

### Post by NewWithoutClue on 2006-08-12
Software holes are found and fixed faster in the open source community than they are in the closed source one. What this means is that, if there is a hole in a piece of software, someone with the know-how can either A) report the problem or, B) keep it a secret and use it for 'evil'.. but that's just one person.. chances are some other guy will come along the problem pretty soon and choose the right path and report the problem to the software devolpers.

Regards,
Paul

---

### Post by aysiu on 2006-08-12
Back up your files regularly.

Don't run as administrator all the time (Windows defaults to administrator; Ubuntu does not without a password confirmation).

Create strong (hard-to-guess) passwords.

Don't be stupid. Don't click attachments on emails. Don't give information away to phishy websites. Disable Javascript and Flash on anything you don't approve (use the NoScript extension in Firefox). Don't open any ports unless you know what you're doing.

---

### Post by FenrisAbraxas on 2006-08-14
> **bjweeks said:**
> Ubuntu doesn't need a firewall because it has no running daemons.

Even if you have no running deamons, someone may have phisical acces to your box and if you installed a buggy app wich let you escalate privileges the attacker can own your box :S remember not all attacks are from internet.

Edit: The question is out-of-the-box, yeah it's more secure but ALL default installs are dangerous and think about this.

Leave you with a MINIMAL system with like 20 programs installed, but a Linux default install have LOTS and LOTS of apps which have to be updated for security reasons.

Example: Ubuntu installs Firefox 1.5.1 (current may be 1.5.2) but a friends Windows CD installs IE 5 (wanna count the security holes in that piece of ....).

---

