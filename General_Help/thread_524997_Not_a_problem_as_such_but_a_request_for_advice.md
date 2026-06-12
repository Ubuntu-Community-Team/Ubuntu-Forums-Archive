---
title: "Not a problem as such but a request for advice"
date: 2007-08-13
forum: General Help
---

### Post by Jim D v2.0 on 2007-08-13
This is sort of a question about partitioning.



First some background.



In the past when I have upgraded from one ubuntu release to the next I have had problems. The on-line upgrade process has been a disaster for me with each new release. So then I had to download the full version and burn it to a CD and do an installation from scratch. This turns out to not be a problem, except that I loose all of my current settings and software installations.



With the Dapper release I created a separate partition for my /home directory (actually it is even on a separate drive from where the OS is located) which made it quite convenient to upgrade without loosing all of my personal data. This works quite well.



Now here is my question.



I would like to set-up additional partitions for other directories. Which directories would make the most sense for this given that when Gutsy is released I plan to do a re-install instead of an upgrade? Or is this not a good idea?



Pros and cons are very welcome.



Thanks in advance for any responses.

---

### Post by raja on 2007-08-13
I keep separate partitions for /boot, / and /home. I know some people would have a separate partition for /var and of course you can put a lot of things on different partitions, but you get into problems with judging how to allocate space among them.

---

### Post by bjarneh on 2007-08-13
the partitions which are hardest to "restore", ie. you don't wan't to make all your config files and so on one more time so a /home/ partition is nice, you don't wan't to rip all your cd's or download all that music again so a /var/multimedia for such and so on can be quite handy :-)

---

### Post by shad0w_walker on 2007-08-13
Depending on the school of thought splitting every base folder (/etc,/tmp,/lib, etc) is a good idea, i personally would only bother with the home folder personally, unless you have a reason to bother with more partitions. Keep it simple and theres less that can screw up.

---

### Post by HermanAB on 2007-08-13
It depends on your situation.  For a desktop machine it is probably OK to have /, /swap and /home.  For a server, it is better to split out /var, /tmp and /usr also.  

The reason is to limit damage when things go wrong and to make it easier to do upgrades.  Having separate partitions also makes it easier to encrypt the data partitions.  (There is no point in encrypting system partitions.  Ubuntu is Free and anybody can read the source code, so it just makes the machine slow if you encrypt system areas.).

I hope that helps!

Herman

---

### Post by Jim D v2.0 on 2007-08-14
Thanks to you all, I appreciate the responses.

Since this is a desktop and not a server I will leave things as they are and maintain just my /home directory as a separate partition.

---

