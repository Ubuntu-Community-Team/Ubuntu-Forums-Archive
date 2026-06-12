---
title: "dapper adept dies just before committing changes"
date: 2007-11-17
forum: General Help
---

### Post by duojet on 2007-11-17
I ran adept-manager yesterday to update my dapper install. for whatever reason, I was able to start it, select full upgrade and even manage repos to make sure there were no conflicts. The only problem came when I was trying to actually COMMIT. No GUI error messages, nothing, just "preparing to commit packages" then - pfft!

Interestingly, running apt-get presented no problems at all, so I've actually already updated everything, no emergency really, I would just really like to figure it out.

---

### Post by aysiu on 2007-11-17
Close Adept. Make sure *apt-get* or Update Manager is not running.

Then, paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
kdesu adept
``` When Adept crashes, see if the terminal generates any error messages. If so, paste the messages back here.

---

### Post by duojet on 2007-11-17
Running adept under Kdesu allowed me to select/deselect and install packages with no problem.. as well as using the regular GUI after that. I don't have any updates at the moment, but I'll post again if this still happens.

I'm kinda confused but things seem to be working, so I guess I can't argue. 

BTW, Aysiu, I really appreciate all the things you've done on the forums.. aside from your replies to my posts, a lot of your HOWTOs and tutorials have been extremely useful!

---

### Post by aysiu on 2007-11-17
I'm glad you've found my help useful in the past. I hope it works for this, too.

If *kdesu adept* works, perhaps you should double-check that the menu icon for Adept has that command in it.

---

