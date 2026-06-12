---
title: "run my own pop email system?"
date: 2007-05-09
forum: General Help
---

### Post by silent1643 on 2007-05-09
somewhat still new to linux but i understand alot so far... is there anyway to run my own pop email account from my machine? im on a cable modem and i would think that should be enough speed for this, but what else would i need? static ip or is there another option? software recomendations?

---

### Post by strixy on 2007-05-09
> somewhat still new to linux but i understand alot so far... is there anyway to run my own pop email account from my machine?

Step 1: Visit a psychologist...

you must be crazy

Step 2: look into Exim4, Spamasassin, Pop3 and 

[http://ubuntuforums.org/showthread.php?t=393683](http://ubuntuforums.org/showthread.php?t=393683)

---

### Post by silent1643 on 2007-05-09
> **strixy said:**
> Step 1: Visit a psychologist...

you must be crazy

Step 2: look into Exim4, Spamasassin, Pop3 and 

[http://ubuntuforums.org/showthread.php?t=393683](http://ubuntuforums.org/showthread.php?t=393683)

lol why must i be crazy, im guessing its to hard huh :D

---

### Post by strixy on 2007-05-09
Nah... setting it up is relatively easy if you've got some time invested as a sys admin. It's the amount of time it takes to do it properly and the time it takes to learn what all of the configuration options mean.

I guess I am of two minds. The first is that anyone should be able to copy/paste lines out of a "how to" and get it going. It takes a little insanity to really ~learn~ how to set it up without a "how to" guide, especially someone who is new to linux. You're either copy/paste crazy or just plain crazy... either way, your crazy.

Further madness... It's not hard to get an email server set up. It's getting one locked down securely so the spammers don't end up chowning your server. It's waking up in the middle of the night worrying if you set some bit to "on" or "off" and if "on" means that somewhere, some hacker is now relaying 110,000,000 spam emails through your server. Oh, and Is your ISP tracking your bandwidth and are they about to send you a bill for $23,456 in bandwidth overages? Did I forget to mention that every time you hear about a virus in the news you go to work... regardless of what time it is? or what day of the week it is? How about those 3am phone calls from people who can't check their email because your power went out? Or forgetting (or not knowing) that you really should have a secondary MX record directing undeliverable email to a backup holding server. Or accidentally setting all undeliverable mail for 12 domains - to _your_ email box - maxing out it's 2gig limit in little over an hour long lunch break. Or creating an accidental delivery loop!

Anyone who mucks about with an email server has my deepest respect, but ya'll 're 10 kinds o'crazy!

I think I'll stick to safer hobbies like snowboarding, down hill mountain biking and scuba with sharks.

---

### Post by IgnorantGuru on 2007-05-09
In case you want a really simple one, you can just install popa3d.  There is no config - it simply lets users connect and retrieve their system mail via pop3.  So each pop user must be a user on your system.

It is a primitive solution but works well for having a private mail system on home/office lans.

As for sending mail, it's probably easier to run postfix - fairly easy config.

And if you want to run an IM server, check out Wildfire (which is a jabber server).  Good for a private IM system on a lan.  You can use Gaim/Pidgin for the clients.

---

