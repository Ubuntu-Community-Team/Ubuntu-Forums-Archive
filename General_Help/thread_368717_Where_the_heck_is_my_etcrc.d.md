---
title: "Where the heck is my /etc/rc.d??"
date: 2007-02-23
forum: General Help
---

### Post by pebkac on 2007-02-23
yes i did a search, but I didn't find any results on this which is most likely a very simple thing.

I have a new server that has Ubuntu edgy on it (NO GUI is installed). It is replacing a Mandrake server.

My mandrake server has some commands that I added to /etc/inittab and /etc/rc.d for example a custom firewall/iptables script; also I added some commands to rc.local for the UPS and for Apache (simple things like service httpd start and 'echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_all') - all these things are executed at boot time.

My ubuntu server does not have an /etc/inittab or /etc/rc.d so I do not know where to put these things. (Yes I know that most of the Mandrake stuff will not apply to Ubuntu but my firewall is very important).

If it matters my Mandrake computer uses lilo and my ubuntu uses grub.

Thank you.

---

### Post by llamakc on 2007-02-23
Ubuntu uses Upstart. You can read /usr/share/doc/upstart/README.Debian.gz which does a great job of explaining where stuff is.

/etc/inittab is now replaced with the contents of /etc/event.d/, and there are rc[0-6].d directories inside of /etc.

---

### Post by bobpaul on 2007-02-23
Well, to do it "correctly" you should add a new script to /etc/init.d and use update-rc.d to add it to the proper runlevels.
```
man update-rc.d
``` 
You can look at other scripts in that folder as an example, or read
```
man start-stop-daemon
```

For a quick and dirty fix, make a script anywhere. I like /root/scripts. Then symlink it to the proper runlevel folder. IE, for a script "firewall"

```
ln -s /root/scripts/firewall /etc/rc2.d/S99firewall
```

Don't forget to make the script executable!

OOPS! I took too long to reply! ;) And the previous answer is better. I haven't mucked down there since dapper... forgot about upstart :*)

---

### Post by pebkac on 2007-02-23
Thank you both for the replies! I am leaving for the day but I will be sure to try this on Monday, thanks!

---

