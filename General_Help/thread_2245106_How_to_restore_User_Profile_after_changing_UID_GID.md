---
title: "How to restore User Profile after changing UID GID ?"
date: 2014-09-21
forum: General Help
---

### Post by blnl on 2014-09-21
In order to align UID GID with my other (NFS mounted) systems, I have changed UID GID of Ubuntu user.

These are exact steps that I performed to change UID GID of user "boris":
[LIST=1]
[*]log-out user "boris"
[*]Ctrl+Alt+F2
[*]log-in as root
[*]execute following commands:
[/LIST]
```
cp /etc/passwd /etc/passwd.bak
cp /etc/group /etc/group.bak

groupmod -g 702 users
usermod -u 502 -g 702 boris 
groupdel boris

find / -user 1000 -exec chown -h 502 {} \;
find / -group 1000 -exec chgrp -h 702 {} \;

reboot -f --verbose
```

After reboot I can still log-in as user "boris", everything seems to be normal (home directory is recognized, NFS drives are mounted, screen background is there, program shortcuts work properly), but I noticed that the User Profile (in System Settings > User Accounts) has disappeared.
[IMG]http://home.telfort.nl/chaos_and_order.com/Ubuntu/User_Accounts-bad.png[/IMG]

As you can see in the screen-shot above, there is no user profile at all (although while making the screen-shot I'm logged in as user "boris"). Yet it used to be something like this before:
[IMG]http://home.telfort.nl/chaos_and_order.com/Ubuntu/User_Accounts-good.png[/IMG]

As User Profile for user "boris" is not in there, I can only conclude that UID GID migration was not 100% successful.
Which step(s) am I missing in order to migrate UID GID correctly?

By the way, I'm doing this standard on my Fedora systems and it never fails.
Something is different in Ubuntu... But what is it?

Does anyone have an explanation what went wrong?

---

### Post by HermanAB on 2014-09-21
After changing the IDs, I would simply do:
# cd /
# chown -R boris: /home

---

