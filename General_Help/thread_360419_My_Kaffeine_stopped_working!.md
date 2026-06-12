---
title: "My Kaffeine stopped working!"
date: 2007-02-13
forum: General Help
---

### Post by Morientes on 2007-02-13
On my Kubuntu 6.10 suddenly my kaffeine player just wont start. Absolutely nothing happens when I try to start it! If I start it in a terminal, it outputs nothing.
I have NO idea what has caused this. It was working yesterday and today it is not! I have also tried to reconfigure it and to reinstall it, but it does not help. The only thing I have played a little around with is my phones bluetooth remote control, but I used that yesterday also and it worked then.
Does anyone know what is wrong?

---

### Post by kenmiles on 2007-02-13
Try in a command window
skill kaffeine
then restart Kaffeine.
Regards, Kenneth

---

### Post by Morientes on 2007-02-13
eh ok, that worked, thanks a lot!

Can you tell me what was wrong? And what did that skill command do?

---

### Post by itazuki on 2007-02-14
Thank you very much for this solution kenmiles! I started having this problem this morning.

According to [http://linux.about.com/library/cmd/blcmdl1_skill.htm](http://linux.about.com/library/cmd/blcmdl1_skill.htm), skill sends the process to the TERM Signal. The TERM signal's default current disposition (what happens to the process when it is delivered to the Signal) is to terminate the process.

It is strange because I rebooted multiple times since I started having this problem so this should've killed the process if the cause of this issue was because there was already an instance of Kaffeine running. Because of this there must be more to the TERM signal or the skill command than I am aware of and/or this problem was not just caused by multiple instances of Kaffeine running.

---

### Post by kenmiles on 2007-02-15
> **itazuki said:**
> Thank you very much for this solution kenmiles! I started having this problem this morning.

According to [http://linux.about.com/library/cmd/blcmdl1_skill.htm](http://linux.about.com/library/cmd/blcmdl1_skill.htm), skill sends the process to the TERM Signal. The TERM signal's default current disposition (what happens to the process when it is delivered to the Signal) is to terminate the process.

It is strange because I rebooted multiple times since I started having this problem so this should've killed the process if the cause of this issue was because there was already an instance of Kaffeine running. Because of this there must be more to the TERM signal or the skill command than I am aware of and/or this problem was not just caused by multiple instances of Kaffeine running.

I dont's know the reason why but re-booting never kills the process when this fault happens, I aso lost sound one time and this was the only way I found to recover it.
Having said that I find Kaffeine is the best program that I have used for my TV card, even outperforms Showshifter in windows.
Regards, Kenneth.

---

### Post by Morientes on 2007-02-15
I just had the error again. skill solved it again also.

Still it is a strange error. I guess it must have to do with the fact that kaffeine does not shut down properly and then, when in KDE, things that are running when shutting down the computer, are started again when it boots up next time.

---

