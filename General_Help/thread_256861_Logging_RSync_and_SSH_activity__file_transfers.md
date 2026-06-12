---
title: "Logging RSync and SSH activity / file transfers"
date: 2006-09-13
forum: General Help
---

### Post by feenster on 2006-09-13
Hi all,

I have a Ubuntu 6.06 server that I am using to RSync files onto via SSH. I currently have things setup so that the client machine logs what data has been transferred into a text file, which is RSync'ed to the server after the main transfer has completed. 

This isn't ideal - is there any way I can get the RSync or SSH Daemons to log which users have connected into their own file (not just into syslog), and tell me what files have been transferred overnight?

Cheers,
 Matt

---

### Post by lamego on 2006-09-13
Have you tried to add a rule at /etc/syslog.conf to achieve that ?
I am not sure you have a pattern than can be filtered with syslog conf rules...

---

### Post by feenster on 2006-09-16
Humm, I'm not really sure of the syntax for doing that. Any chance you could you elaborate on it a bit for me? I'm a bit of a newbie at the moment :S

Matt

---

