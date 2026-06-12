---
title: "Synantic Is it true ?"
date: 2005-05-21
forum: General Help
---

### Post by Swazi on 2005-05-21
Hi

After playing around with the live cd's and installing to harddrive a couple of times i was unimpressed with Ubuntu Hoary. Till i installed from the DVD and used the unofficial add on cd.

Wow what a diifference, i have all my multimedia working now, i am becoming familar with apt and dpkg and i see there is a nifty package management system called synantic.

My question is when i choose all it tells me that there are 15873 packages available for downlaod, is this a typo or is this true ?

Ubuntu rocks when you know what you are doing, great job guys :-)

Sidenote: Just got to get root login to work for webmin now and mission accomplished, i searched the forum but the answers there did not solve my problem i still get access denied.

---

### Post by jasmuz on 2005-05-21
[QUOTE=Swazi]Hi

After playing around with the live cd's and installing to harddrive a couple of times i was unimpressed with Ubuntu Hoary. Till i installed from the DVD and used the unofficial add on cd.

Wow what a diifference, i have all my multimedia working now, i am becoming familar with apt and dpkg and i see there is a nifty package management system called synantic.

My question is when i choose all it tells me that there are 15873 packages available for downlaod, is this a typo or is this true ?

Ubuntu rocks when you know what you are doing, great job guys :-)

Sidenote: Just got to get root login to work for webmin now and mission accomplished, i searched the forum but the answers there did not solve my problem i still get access denied.[/QUOTE]
 First off, the package list is actually the quantity of files that are available, this includes every package exported to ubuntu by the team. Plus, you can add the backports for more fresher packages wwww.backports.ubuntuforums.org

So you want root? -->have you tried using sudo as a workaround? if so, and you still want root do this.

Open a terminal and the following:

#sudo passwd

This will ask you for your new password, wich you will set for your root account, therefore you can login as root for your webadmin services.

Take care...hope to hear if this solves your questions.

---

### Post by nix4me on 2005-05-21
Thats true.  You certainly do not want to install everything.

Use the sort features to look at groups of packages that you might be interested in.

Mark

---

