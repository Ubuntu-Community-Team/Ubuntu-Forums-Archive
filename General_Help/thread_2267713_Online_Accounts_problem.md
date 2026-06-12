---
title: "Online Accounts problem"
date: 2015-03-03
forum: General Help
---

### Post by Mick21367 on 2015-03-03
Hi,
I've recently been messing about with adding ldap accounts to my ubuntu 14.10 install. As part of that I migrated my home folder contents to my new ldap account. Pretty much worked OK, the only problem now remaining being online accounts. If I open Empathy (for example), I get the message 'You need to setup an account to see contacts here' - online accounts then opens, and lo and behold, my google account is there. However, it has no effect. If I click on options against the Empathy entry (in online accounts), I *should *be able to edit my Google account details, but the window stays stubbornly blank. I appear to be able to add any account (Windows Live, Facebook, Google, etc) but seem to be totally unable to actually access any of them from e.g. Empathy, or from within the Options button in Online Accounts. It's hardly going to keep me awake at night, but does anyone have any idea how I can either fix this, or reset the online accounts utility to start again?
I should say at this point that Online accounts still works OK on my local account (which I kept for emergencies ;) ). Also, I've tried uninstalling and reinstalling Empathy and the Online Accounts utility (unity-control-center-signon).

Thanks

Mick

PS Ubuntu is 14.10 (unity) - really must update my profile sometime :-)

Two days later - I've discovered that the same issue affects my laptop - ldap users seem to be unable to connect through online accounts. Local users are fine. Well, at least it narrows it down a bit :-)

---

### Post by Mick21367 on 2015-03-21
Might have found out *why *this happens - mentioned in this thread ([http://ubuntuforums.org/showthread.php?t=2228850](http://ubuntuforums.org/showthread.php?t=2228850) - pauljwells reply) non-standard home folders may have problems. My ldap users' home folders are located in /home/users/user. Not sure if it's worth the effort of pursuing a fix for myself as there are plenty of alternatives to empathy. Anyway, if anyone is having similar problems, hope this helps a bit :-)

---

### Post by Mick21367 on 2015-03-22
Found a solution - please see this bug report here ([https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/994926](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/994926)) - basically follow post #13, as follows:-
sudo dpkg-reconfigure apparmor
add additional home folder locations as required - in my case I added /home/users/ (remember the trailing /)
worked perfectly - empathy now reads the online accounts and opens as normal :-)

---

