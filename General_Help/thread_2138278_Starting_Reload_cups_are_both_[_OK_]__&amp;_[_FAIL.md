---
title: "Starting Reload cups are both [ OK ]  &amp; [ FAIL ] at boot"
date: 2013-04-23
forum: General Help
---

### Post by clearski on 2013-04-23
One of the first things I did after I installed 13.04 was to remove *modemmanager*, because I don't use it. However, I noticed that during the boot process there was still a reference to this:

**Stopping modem connection manager [ OK ]**

By chance I went to /etc/init/, made a copy of *modemmanager.conf*, preserving permisions, time stamp, owner etc. and deleted the file from the init/ folder. After restart, the reference disappeared from the boot screen, so I believe that the problem was fixed and not only apparently.

But I still got one more problem:

 [B]* Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                   [OK]

 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                   [fail][/B]

This reference appears twice. I looked into /etc/init and there *were* :) two files related to cups. The first was *cups-browsed.con*f (I also deleted cups-browsed a long time ago :) ) and *cups.conf*, but removing *cups-browsed.conf* didn't solve the problem. I still get the FAIL message.

Any ideas about why I'm getting this and how can it be fixed? 

Thank you.

---

### Post by tgalati4 on 2013-04-23
Ah yes, the tempation to remove stuff from linux.  Unlike Wikipedia, an idea that seems better on paper than in practice.

The avahi daemon is used to advertise your shared printers on the network.  Removing those configuration files will break the services that rely on them.

You can reinstall cups or replace those configuration files and reboot.

Configuration files are meant to be configured--not deleted.  If they were meant to be deleted they would be called *delete_me* files.  You can safely remove any files called *delete_me*.

---

### Post by clearski on 2013-04-24
It might have to do with some cups files I removed with apt-get... I can't remember if the message appeared twice right after the installation of OS. I'll give it a try and install cups-browsed & cups-bsd and put back the files in .conf, to see if there's a change.

Thanks!

---

### Post by jasmines on 2013-05-04
Same issue here, after upgrade to 13.04. Any chance to get it solved?

---

### Post by JonPaul on 2013-05-07
Same here..... haven't done anything funny with printers

---

### Post by creosote on 2013-05-07
It's not a result of having removed anything. Linux has great tools for safely removing unused software.
There's a bug filed for the CUPS reload: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1158686](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1158686)

---

### Post by crysman on 2013-10-26
> **clearski said:**
> ...

But I still got one more problem:

 [B]* Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                   [OK]

 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                   [fail][/B]

This reference appears twice...

Same issue here, and I have just done a clean install (Xubuntu 13.10). I have had disabled the modem manager the way described here [[http://forums.linuxmint.com/viewtopic.php?f=42&t=101010&start=0]](http://forums.linuxmint.com/viewtopic.php?f=42&t=101010&start=0]), **but I've had this error already even before doing so**! That means this issue is not dependent on any removal or non-standard user behavior!

See my boot.log:
```
$ cat /var/log/boot.log 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles                                                   * Starting SystemD login management service                                    [ OK ]
[ OK ]
 * Starting mDNS/DNS-SD daemon                                                 [ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                   [ OK ]
 * Setting sensors limits                                                      [ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                   [fail]
 * Setting up X socket directories...                                          [ OK ]
 * Stopping System V initialisation compatibility                              [ OK ]
 * Starting network connection manager                                         [ OK ]
 * Starting System V runlevel compatibility                                    [ OK ]
 * Starting                                                                    [ OK ]
 * Starting                                                                    [ OK ]
 * Starting cups-browsed - Bonjour remote printer browsing daemon              [ OK ]
 * Starting Restore Sound Card State                                           [ OK ]
 * Starting ACPI daemon                                                        [ OK ]
 * Starting anac(h)ronistic cron                                               [ OK ]
 * Starting                                                                    [ OK ]
 * Starting                                                                    [ OK ]
 * Starting save kernel messages                                               [ OK ]
 * Starting                                                                    [ OK ]
 * Starting                                                                    [ OK ]
 * Starting automatic crash report generation                                  [ OK ]
 * Stopping save kernel messages                                               [ OK ]
 * Stopping Restore Sound Card State                                           [ OK ]
 * Stopping Restore Sound Card State                                           [ OK ]
 * Starting regular background program processing daemon                       [ OK ]



```

---

### Post by clearski on 2013-11-10
I switched to 13.10 with a clean install last night and one of the first thirty :) things I did was a

```
sudo apt-get purge cups*
```

It's really good for the Desktop edition, but I am simply not using it for now.

After reboot, the error was still there and it stayed there until I did this:

```
sudo apt-get purge avahi*
```

Now I've got a clean boot process.

Please note that:

a) I am using static IP addresses (**no DHCP**);
b) I run a DNS server over LAN;
c) I was ready for a reinstall.

It's not exactly a *"do this"* post, only a report of how I got this solved in certain circumstances.

---

