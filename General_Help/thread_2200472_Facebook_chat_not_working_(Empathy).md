---
title: "Facebook chat not working (Empathy)"
date: 2014-01-19
forum: General Help
---

### Post by ijhm86 on 2014-01-19
Everytime I try to go online, the following message appears:

"Applications can no longer acces your [xxx@gmail.com] Online Account."

I granted access and all that. What's wrong with my Online Account?

Thanks in advance.

---

### Post by richardsdma on 2014-01-21
if we are talking about main ubuntu, i have the same issue: empathy does not work with facebook chat. 
but let me tell you a short story:
few days ago, i have installed ubuntu-gnome that also came with empathy. when i have tried to setup the account, empathy offers me to install some extra packeges. i have wait a little, i setup the accounts and the facebook/gmail/yahoo chat was working fine. after that, i installed that extra packeges that they have offered to me few moments ago. after that, the ubuntu online accounts icon have been added on the setting. i have log off from empathy chat and tried again. this time around, tha facebook chat did not work anymore.  
next day, due to the fact that i was forced to reinstall ubuntu-gnome (an evolution packege problem), i needed to setup empathy again. i have setup the accounts and again, the system offers me to install thet extra packeges. this time, i have just ignored them. i can thell you that this time, the empatny is working fine. 
so, the problem seems to be the fact that "ubuntu online accounnts" somehow impairs empathy of working good.

LATER EDIT:
i just tried on my ubuntu: 
first of all, remove ubuntu-online-accounts.
> sudo apt-get purge gnome-control-center-signon
then, delete the accounts for empathy in: /home/youur-user/.config/libaccounts-glib/accounts.db and /home/youur-user/.config/libaccounts-glib/accounts.db-journal, reboot and then, go to unity desktop, press alt+f2, and write "empathy-accounts". create new accounts. this have worked for me.
of course, you can install and use pidgin instead of empathy.

---

### Post by ijhm86 on 2014-01-23
Hey, thanks for the reply!

I will try that and see if it works for me as well!

---

