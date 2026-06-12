---
title: "lag while su"
date: 2006-10-19
forum: General Help
---

### Post by marianom on 2006-10-19
Hi there:
 i'm trying to do a "su" to change users in my PC. Although it finally logs in the user it takes more than 30 seconds to verify the password (just like when you submitted a wrong pass, but in this case the pass is ok since I can connect).
The other problem I have is that I cannot ssh this machine from other pc in the net, it finally tells me "Permission denied, please try again." I suspect that this is due to the same lag I'm experiencing while trying to switch users as explained up supra: the ssh finally time out.

If anyone can suggest a way to verify why it takes so long to verify the pass, I'll appreciate.

---

### Post by MWAAAHAAA on 2006-10-19
Is it just the login that is slow, or does it also take a while for the shell to load (assuming you are logging into a CLI environment, if not please try). I usually have this problem when some process(es) are hogging up los of CPU time. Perhaps you have some hungry programs running in the background?

---

### Post by marianom on 2006-10-19
Hi MWAAAHAAA,
 thanks for your reply. It seems this vmware process was running and eating CPU. Killed and uninstalled (I will try it again somday) fixed the issue.

Gracias again and take care.

---

