---
title: "Firefox doesen't like restarting"
date: 2012-10-22
forum: General Help
---

### Post by *^kyfds( on 2012-10-22
I'm not sure whether this is a widespread issue, or just my computer, but almost every time i close firefox, and try to restart it, I get the "firefox is not responding in another window" error message.

I've always had this problem, but it's become more prevalent ever since I upgraded to 12.10.

Is there a workaround?  It's annoying having to kill the application through terminal whenever i want to restart firefox.

Any help is appreciated - 

~THC.

---

### Post by dino99 on 2012-10-22
that should not be the only problem with your config: watch your logs to find usefull errors/warnings (.xsession-errors & /var/log/)

then clean the system:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

be sure to use a clean /etc/apt/sources.list

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
( be patient, it can take a while before ending itself, dont stop it yourself)

---

