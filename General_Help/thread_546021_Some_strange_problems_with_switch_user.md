---
title: "Some strange problems with switch user"
date: 2007-09-08
forum: General Help
---

### Post by Ozor Mox on 2007-09-08
Has anyone else experienced any unusual problems when trying to switch user? I have set up a guest account on my laptop so that someone else can use my computer, and if I'm already logged on I use switch user to let them log in. Locking my account and switching to the guest account works fine, but when I log them out after they have finished, sometimes I get the locked screen password box and all goes well, but sometimes one of two things happens. Either the screen goes plain orange/brown (Ubuntu login colour) and completely freezes (including mouse and ctrl+alt+F1-F8 or backspace) and I cannot get back in to my session without rebooting, or I get back in to my session without a problem, but the little drumbeat sound when the login screen first appears gets stuck on an infinite loop forcing me to reboot before I go mad!

Just me, or is this some kind of weird bug? As far as I can tell, logging out a user before logging in another one is ok, this only happens when switching users and leaving sessions logged in.

---

### Post by anutron on 2007-09-17
I'm having similar issues. I can use ctrl-alt-backspace just fine, but I can't type in the password field. I click the field but focus is not delivered to the field, so I cannot unlock the session...

---

### Post by beyboo on 2007-09-23
Same here - using Feisty. :(

However a word of advice, instead of going for the reset button when its a hard freeze, try using this 

[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

One more reason to love Linux :)

---

### Post by pixeltarian on 2007-09-24
I've been having issues with switch user as well.  I can logout and login to multiple profiles, but I get a video crash when I switch users and then go back to the original user. I think it might have something to do with compiz-fusion. perhaps running two instances of the same plug-in? I can just press ctrl+alt F1 and reboot when it happens though. it doesn't lock up for me or anything. 

I'll just stick to log out for not I guess. fixing it would be nice though...

---

