---
title: "System freeze at shutdown/reset"
date: 2007-08-25
forum: General Help
---

### Post by theh0g on 2007-08-25
I'm running 7.04 and whenever I click shutdown or reset, desktop items clear and when it should start shutting down, it just freezes. Only mouse can be moved, I can't switch to terminal or anything. I think it's Compiz fault, but I don't know how to fix this. Any ideas?

p.s. same thing happens with Gutsy x64 Tribe 4 on another partition.

---

### Post by DapperDanMan on 2007-08-26
I recently installed (K)Ubuntu 7.04 myself. I am having the same problem. When I shutdown it 'freezes'; I end up hitting reset button and at the login screen I issue a Alt-S and it shutdowns from there. I'll keep an eye on your post to see if someone has a resolution.

---

### Post by sirmelle on 2008-02-18
I have the same problem as you. 
Also have compiz installed, but I think that problem could be in ATI's Catalyst drivers . I am not sure, but I think that problem occures to me before I installed compiz, and after I installed those ATI's drivers.

I think that you can shutdown/reset computer using terminal command (shutdown -h now or shutdown -r now), so you can make desktop launcher with that commands. This could be a little help before someone helps us.

---

### Post by sirmelle on 2008-02-19
Finally I found the sollution:

Go to System > Preferences > Sessions
Check Power Manager under Startup Programs tab

That's all!

---

