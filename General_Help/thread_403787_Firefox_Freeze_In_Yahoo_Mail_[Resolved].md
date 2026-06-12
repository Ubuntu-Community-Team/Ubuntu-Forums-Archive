---
title: "Firefox Freeze In Yahoo Mail [Resolved]"
date: 2007-04-07
forum: General Help
---

### Post by shawnerz on 2007-04-07
Hello all.
I did a quick search and didn't see anyone else with my problem.
I am running Edgy Eft on a 666 MHz Celeron with 512 MB of memory.

My problem is when I read my mail in Yahoo mail, Firefox freezes after reading the first email.  I cannot go to the next email, I can't sign out from Yahoo.
If I open a new tab, the connection in the new tab never "connects."  The swirling circle (loading indication) stays on and does not do away.
I have to close Firefox by clicking on the "X."

I would say this is a Firefox problem, but I did not have this problem in Dapper Drake.
 Any ideas?
-Shawn

---

### Post by aysiu on 2007-04-07
Well, there are a couple of ways to try to figure out what's going on.

1. Try a different browser (Opera, Epiphany). See if that also freezes on Yahoo! mail.
2. Try a different user with Firefox. If you don't have a different user, create a new test user (you can delete it later).
3. Launch the command *firefox &* from [the terminal](http://www.psychocats.net/ubuntu/terminal) and go to Yahoo! mail. If Firefox freezes, see if there are any error messages in the terminal. If there are, post them back here (copy and paste).

---

### Post by Swab on 2007-04-07
Are you running any plugins or add-ons?  Trying removing them and see if that helps.

---

### Post by shawnerz on 2007-04-07
Aysiu,
Thank you for the suggestions.  The same problem happens in Epiphany.  I found out the problem is caused by Firestarter firewall.  If I turn Firestarter off, Firefox works fine.

I know this outside of the topic of Firefox, but do you have any idea what seeting in Firestarter might be causing this?
In the ICMP section, I have ICMP Filtering enabled to prevent my computer from responding to pings.
Which service would I unblock to get Firefox and Yahoo to play together nicely?
Thanks,
-Shawn

---

### Post by shawnerz on 2007-04-08
All,
I found the problem.  In Firestarter, Preferences | ICMP Settings, I had to check the 'MS Traceroute' option.  This option allows MS Traceroute packets through the firewall.
Thanks for everyone's suggestions and help.  I guess Yahoo mail needs this information.
-Shawn

---

