---
title: "Evolution Freeze -- Hoary and new account"
date: 2005-04-22
forum: General Help
---

### Post by jMack on 2005-04-22
Greetings-

My Ubuntu currently freezes completely when I open up Evolution.  Whats worse, is that I've defaulted my boot-up so that it auto-loads when I boot/login.  Really, it doesn't freeze; the HD goes on whirlling and can't give me the time of day cuz it's too busy.  If I'm patient, I can close the window (10 mins or so) and work with other apps.

Reason:
As far as I can tell, the "freeze' happened after i created a new mail account, which I believe doesn't have proper pop/smtp settings.  I was trying to determine (by trial and error) how to pull/send mail from work without any luck.

Solution:
I've tried removing the account, but its going on 30 mins where I can't do anything on the machine except watch my curser blink across the screen every 5 seconds as I move the mouse around.  Yay.

Gear:
brand-new Toshiba Satelite Notebook, 1.5ghz Cel, 40gig HD (10 as XP), 512mb Ram, etc etc.  The $500 Best Buy Special they had back in January.

I've done some basic searches, and found no other issue like mine.  Let me know if you have any ideas, as I've never troubleshooted Evolution, and I'm a novice *Ubuntuneer*.

Thanks

---

### Post by jMack on 2005-04-22
Hmmm...

In the bottom of Evolution, it says: 
[quote]Formatting message(...)[quote]

looks like its working a bit better, but its REAL slow.  I'm thinking I should remove then reinstall Evolution to see if that fixes it.  

Still, how do I backup my mail?  I don't see an 'Export' Button.  Can I just copy/move some folders in the .evolution directory and put them back in a new install?

Curious....

---

### Post by Alexander Kirillov on 2005-04-22
[QUOTE=jMack]Hmmm...

In the bottom of Evolution, it says: 
> Formatting message(...)[quote]

looks like its working a bit better, but its REAL slow.  I'm thinking I should remove then reinstall Evolution to see if that fixes it.  

Still, how do I backup my mail?  I don't see an 'Export' Button.  Can I just copy/move some folders in the .evolution directory and put them back in a new install?

Curious....
  AFAIK, the relevant folders are .evolution/mail and evolution/local, but I'd suggest backing up the whole .evolution directory - in case somethign else is needed.

---

