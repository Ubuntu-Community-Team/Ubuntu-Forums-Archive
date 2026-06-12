---
title: "Popfile"
date: 2005-04-08
forum: General Help
---

### Post by inging on 2005-04-08
Anyone had success with this or know about issues?

I installed via synaptic and it will not start, or uninstall.

---

### Post by Horn on 2005-04-10
I'm having the same problem.  It seems that the ubuntu packages don't include any of the default configuration files.  Does anyone have a fix for this?

---

### Post by julius malchovitch on 2005-05-09
[QUOTE=Horn]I'm having the same problem.  It seems that the ubuntu packages don't include any of the default configuration files.  Does anyone have a fix for this?[/QUOTE]

Popfile 0.22.X does not work with libdbd-sqlite-perl 0.33. Look [here](http://popfile.sourceforge.net/cgi-bin/wiki.pl?HowTos/AllPlatformsRequirePerl) .

I installed libdbd-sqlite-perl 0.31 and popfile works perfectly. 
I have an ubuntu package for it if you want it.

---

### Post by goldenboy on 2005-05-25
Hi,
I tried to say ubuntu to use SQLite2 via the configfile, as is it is recommend on the website, but it doesn't seem to work. The popfile thread is terminated immediately after being startet... :-(

If I try to start the version of popfile downloaded at sourceforge.net after adjusting the SQLite statement it works quite fine.

The logfile created by the ubuntu version, which terminates immedialtely, contains nothing of interest:

```
2005/5/25 13:10:53 8050: bayes: 623: Attempting to connect to dbi:SQLite2:dbname=/var/lib/popfile/popfile.db (1)
2005/5/25 13:10:53 8050: bayes: 629: Using SQLite library version 2.8.15
```

Does anyone have an idea how to solve this? Perhaps you could sent me the link to the old SQLite packages, if you still have it handy. But after I installed these, how can I tell ap-get not to update theses packages??

cheers

---

### Post by goldenboy on 2005-05-25
Ok, I figured out that the problem - besides the perl SQLite version - was/is that in the initscript (etc/init.d/popfile) popfile is started with uid popfile. But since it needs to listen to ports below 1024 (i.e. 110) it needs access to these port. By default only root can enable listening to ports below 1024 and if I run popfile as root it works fine.

But how can I allow the user popfile to listen to these ports? Running popfile as root is shurely not the way it's meant to run...

cheers

---

### Post by madjo on 2005-09-07
*bump* does anyone have solution? :) or know any way to install the older version of the Perl SQLite?

still somewhat newbie-ish :) and a bit hesitant to downgrade anything that could break my system... but if I have to, I'd rather have a step-by-step procedure to follow, less chance for me to screw up ;)

---

