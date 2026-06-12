---
title: "Made a mess with firefox and now it does not start :("
date: 2007-10-20
forum: General Help
---

### Post by jobbesat on 2007-10-20
I made a terrible mess, first installing the language pack from mozillaitalia.org, then installing latest version in italian (2.0.0.8 ) on another dir /opt/firefox), then i deinstall via terminal with command
apt --purge remove firefox
then i reinstalled it via "Add/Remove", but now it doesn't work, because when i click on bar icon it splits "Failed to execute child process "/usr/bin/firefox" (No such file or directory)"
If I type firefox on a terminal, I got:
> The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
bash: firefox: command not found
but when i type the command
sudo apt-get install firefox
I got
>              
firefox is already at the most recent version.
0 updated, 0 installed, 0 to remove and 0 not updated.

Is there a way (via terminal, synaptic, everything else) to make it work?
Thanks a lot in advance

ps: I also tried to completelly remove firefox from synaptic, deleted /opt/firefox dir and reinstall from scratch via synaptic, but still get the same error
pps: if i launch the command
whereis firefox
I get this:
firefox: /usr/bin/firefox.ubuntu /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz

---

### Post by thelocust on 2007-10-20
try typing firefox-bin in terminal

---

### Post by thelocust on 2007-10-20
Also your deb file which is what makes synaptic think it's installed is in your /var/cach and then look around I dont remember the exact folder.

---

### Post by jobbesat on 2007-10-20
ok, thanks

---

