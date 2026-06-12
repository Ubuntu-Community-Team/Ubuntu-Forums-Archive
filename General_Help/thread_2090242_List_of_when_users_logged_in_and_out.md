---
title: "List of when users logged in and out?"
date: 2012-12-01
forum: General Help
---

### Post by Lyuokdea on 2012-12-01
Is there a list of when users have logged in and out of your computer (over the past month or so?)

I have a small linux server, hosting about 10 users - and some odd account activity was reported from the computer about 3 weeks ago (i just heard about it today). The activity might indicate that one of the accounts is compromised (multiple VPN connections with other computers were being attempted). I want to see which users were logged in when the activity occurred. I don't have any special software on my computer - but maybe linux does this automatically somewhere?

If not - what should I install to get this info in the future.

Thanks,

~Lyuokdea

---

### Post by dniMretsaM on 2012-12-01
I believe the command [FONT=Courier New]last[/FONT] will do what you want. You can specify what time to look at as well. Check the man page for details.

---

### Post by SeijiSensei on 2012-12-01
Look in /var/log/auth.log on Debian/Ubuntu or /var/log/secure on RedHat/CentOS.

---

### Post by Lyuokdea on 2012-12-01
Thanks for the info - unfortunately, this only seems to go back a week, so it doesn't have the data I need.

Is there another side system that might have this info? Also useful would be a list of where ssh logins originated from?

Thanks,

~Lyuokdea

---

### Post by SeijiSensei on 2012-12-01
Logs get rotated once each week.  Do you see a /var/log/auth.log.1 or perhaps an /var/log/auth.log.1.gz?  That's last week's log.  The standard configuration (see /etc/logrotate.d) is to keep four weeks' worth.

---

