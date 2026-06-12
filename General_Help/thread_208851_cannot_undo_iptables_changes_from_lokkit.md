---
title: "cannot undo iptables changes from lokkit"
date: 2006-07-04
forum: General Help
---

### Post by eyephisc on 2006-07-04
Hi,

I'm running dapper 6.06 and decided that i wanted to run a firewall.  So i installed lokkit the other day.  Unfortunately, after rebooting, I could not access any web pages.  So I found some advice, where I could issue the commands:

```

iptables -F
iptables -X
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -T FORWARD ACCEPT

```

and then everything worked fine... until I reboot.  I have tried uninstalling lokkit and even removing it with purging all files.  But still, when I reboot, my iptables reverts to NOT allowing me to access the web.

Another temporary solution I found (besides the above commands) is installing firestarter.  After I boot, the web doesn't work.  But if I startup firestarter, it restores web access for me.  I guess it fixes iptables when it starts up.

So is there any way for me to undo whatever lokkit did to my startup files that makes iptables block web access for me?

thanks!

---

### Post by eyephisc on 2006-07-04
Well, I've accepted that I need to just start firestarter each time.  But I noticed that there is a script in /etc/init.d for firestarter and my networking is fixed if I run it:

```
/etc/init.d/firestarter start
```

Then my question is: why isn't this script starting automatically since it's showing a priority of 20 runlevels 2 through 5.  I thought maybe it's trying too early, so I switched it's priority to 99 in these runlevels (using the gui BUM).  Still, the firestarter script does not start on its own.

Any ideas?

---

