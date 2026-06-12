---
title: "spamassassin half  working ... after upgrade to 14.04LTS"
date: 2015-12-27
forum: General Help
---

### Post by rebeltaz on 2015-12-27
Hi again guys... new problem. After upgrading to 14.04LTS, if I tried to mark a message Junk from within Evolution, it complained that a spam program was unavailable. Sure enough, there was no entry in the Plugins for SpamAssassin nor could I find any evidence for SA on my system using dpkg, which or even the Synaptic Package Manager. I closed Evolution and installed SpamAssassin through apt-get. When I reopened Evolution, I was once again able to mark messages as junk and they are moved to my Junk folder, even though SA still does not appear in the Plugins. I read that it may take a couple of hundred Spam/NotSpam marks before SA will function correctly, but even after several hundred "learning" sessions, SA still is not working properly. It will catch a few messages as spam, but it leaves just as many as it finds. Not only that, but it refuses to mark messages junk that I have explicitly marked as spam and it continues to mark messages spam that I explicitly marked as not-junk. 

Any ideas? So far you guys have been on a roll :)

---

### Post by claracc on 2015-12-27
You have to edit file : /etc/default/spamassassin and locate line:

# Change to one to enable spamd
ENABLED=0

and modify it to :

# Change to one to enable spamd
ENABLED=1

Then you start the daemon running in a xterm:

```
sudo /etc/init.d/spamassassin start
```

As ubuntu guide indicates, in the following sessions it will start automatically. If evolution is running you have to restart it.

---

### Post by rebeltaz on 2015-12-27
OK.. I just did that. I killed all evolution processes and restarted that. Now, should I see SA in the Plugins or no? If so... I don't. If no, ten I'll have to let it run for a while to see if it worked. Thank you for the quick response though!

---

### Post by claracc on 2015-12-28
I don't think you can see spamassassin in Plugins ( I cannot see it), but in evolution preferences, mail options, spam flag you can see the possibility to do remote tests with it ( you can try to tick in it to see what happens but a slower runing is adviced).

In a xterm you can try ```
ps -ef | grep spamd
```

I obtain:

```
root      1467     1  0 07:21 ?        00:00:02 /usr/sbin/spamd --create-prefs --max-children 5 --helper-home-dir -d --pidfile=/var/run/spamd.pid
root      1529  1467  0 07:21 ?        00:00:00 spamd child
root      1530  1467  0 07:21 ?        00:00:00 spamd child
clara     3200  3185  0 07:32 pts/0    00:00:00 grep spamd

```

So, I suppose spamassassin is runing

---

### Post by rebeltaz on 2015-12-29
Yeah, the SA daemon is running and it seems to be working now, so I thank you my friend!

---

### Post by claracc on 2015-12-29
You are very welcome

---

### Post by rebeltaz on 2015-12-31
Well... I guess I spoke to soon. spamd IS running, but it still isn't working right. Messages marked spam are still not being moved to Junk when they come in and messages marked as not spam are still being moved to Junk when they come in.

Yeah... spamassassin still isn't working right. I ran sa-update, but that didn't help either. The reason I am curious about SA not showing up in the Plugins is this - [https://help.ubuntu.com/community/HowToEnableSpamFilteringInEvolution]("https://help.ubuntu.com/community/HowToEnableSpamFilteringInEvolution") - and the fact that it was in the plugins before the "upgrade" to 14.04....

I wanted to add this screenshot of Evolution (v.2.28.3) running under 10.04LTS showing that SA does show up under the plugins on that install... which it still is not under 14.04LTS...

[ATTACH=CONFIG]266539[/ATTACH]

---

### Post by claracc on 2016-01-05
It seems there is a bug in ubuntu with spamassassin and evolution and it doesn't seem to be fixed in ubuntu 14.04. Please see: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1247366](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1247366)

---

### Post by claracc on 2016-01-05
There is a ppa for spamassassin which says that have backported the fix in spamassassin package to trusty: [https://launchpad.net/~lvillani/+archive/ubuntu/spamassassin/+packages](https://launchpad.net/~lvillani/+archive/ubuntu/spamassassin/+packages)

---

### Post by rebeltaz on 2016-01-05
> **claracc said:**
> There is a ppa for spamassassin which says that have backported the fix in spamassassin package to trusty: [https://launchpad.net/~lvillani/+archive/ubuntu/spamassassin/+packages](https://launchpad.net/~lvillani/+archive/ubuntu/spamassassin/+packages)

nevermind... let me read that again after having a cup of coffee.

---

