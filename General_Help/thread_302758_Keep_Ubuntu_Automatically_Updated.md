---
title: "Keep Ubuntu Automatically Updated"
date: 2006-11-19
forum: General Help
---

### Post by MonkeyWrench32 on 2006-11-19
Forgive me if this has been asked elsewhere, but I could not find my answer through much searching.

I want to install a copy of Edgy on my dad's PC (replacing XP).  All he does is surf the web and e-mail.  I'd like to know if there was some way I could configure Ubuntu to automatically update itself silently (without any notifications or window pop-ups) that wouldn't require entering in the root password.

Thanks in advance.

---

### Post by Ramses de Norre on 2006-11-19
Although this isn't the safest thing to do, you could accomplish it by setting up a cron job which runs ```
aptitude update && aptitude -y dist-upgrade
```
If you set this in root's cron, it wont need sudo.

---

### Post by TLE on 2006-11-19
All though I know this isn't exactly what you asked I'm going to suggest it anyway.
Depending on how paranoid you are, there is another options. You can just disable the update notifications, so your farther doesn't get bothered by them and the just update the machine when you visit. This do off course mean that he doesn't get security updates ASAP but for a home computer running Linux I wouldn't consider that a risk.

---

### Post by MonkeyWrench32 on 2006-11-19
I think I will go with just disabling the notifications and doing it manually.  I could also SSH to his machine if he's having any problems.

Thanks for the advice.  :)

---

