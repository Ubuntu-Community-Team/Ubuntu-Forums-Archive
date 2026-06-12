---
title: "Application Error*Ubuntu newboy*"
date: 2008-02-05
forum: General Help
---

### Post by Nalced on 2008-02-05
I’m brand new at the Ubuntu world. My friend installed Ubuntu and told me to join the future.

When he was installing it, downloading stuff (no idea what) it was meant to give my laptop the ability to run DVDs. Internet went dead, and the installing-download froze.

Now, I can’t get into Application Add/remove programs thing. It tells me there’s an error and I should go to the synchronized (not sure if that’s how you spell it).

When there, gave me another error.
“E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please rep”

I went to the console or “Terminal”. Put that in, then said. I need to be a superuser to get it done or something. I’m lost and no idea how to fix it, that I’ve been only using it for about 2 hours. Tomorrow I’m gona get my friend to re-install Ubuntu. So, in the next 24 hours advice to fix it would be nice, like a recovery thing like in XP.

Thanks, Nalced (Virgin Ubuntu User)

---

### Post by p_quarles on 2008-02-05
You need to use sudo with that command:
```
sudo dpkg --configure -a
```
Following that, enter your password and the command will run.

---

### Post by Nalced on 2008-02-05
Thanks. I'm shocked at how it kinda self healed. Thank you. I only had some problems with the password, i thought my computer was broken or something. 
But i think it works fine now. Thanks. Ubuntu is the future.

---

