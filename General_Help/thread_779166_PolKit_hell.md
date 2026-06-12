---
title: "PolKit hell"
date: 2008-05-02
forum: General Help
---

### Post by jamyskis on 2008-05-02
I've been having untold problems with my PC since my upgrade to Hardy, and my research has led me to the conclusion that PolicyKit is to blame. Please inform me of the person that authorised this ill-advised inclusion in an LTS release so that I can stuff raw chicken up his nostrils.

The problems I've been having are as follows:

* Can't access authorisations GUI (actually, I can, but only with sudo)
* Can't access network-admin, users-admin etc, as unlock doesn't do anything. Not running any of these tools with sudo results in "The configuration could not be loaded"
* Can't play DVDs with Totem - complains that the HAL daemon cannot be loaded.

I've found the Authorisations GUI, but which authorisations do I change. This is all completely new to me and is a far cry from the simplicity of the groups that I'm used to...

Help?

Thanks!

---

### Post by chrisccoulson on 2008-05-02
Just because you're having issues with it doesn't mean most people are using it without problems. Reading [**_here_**]("https://wiki.ubuntu.com/DesktopTeam/Specs/PolicyKitIntegration") might give you an idea why Policykit is included.

In response to your problems:
[LIST]
[*]What is the output of polkit-gnome-authorization when you run it from the terminal as a normal user?
[*]Is the HAL daemon actually running? (look for a precess called hald)
[*]Can you have a look in your logs (located in /var/log) to see if there are any pointers
[/LIST]

Unless you've played around with the authorizations, you shouldn't need to change any of them to get basic system functionality to work

---

### Post by jamyskis on 2008-05-02
Hi Chris, and thanks for the reply...

> **chrisccoulson said:**
> Just because you're having issues with it doesn't mean most people are using it without problems. Reading [**_here_**]("https://wiki.ubuntu.com/DesktopTeam/Specs/PolicyKitIntegration") might give you an idea why Policykit is included.

I seem to see that it's a recurring problem among people who upgraded from 7.10 (like myself). I appreciate the benefits of PolicyKit, however it is an extremely radical change for a version that is actually supposed to be safe and stable.

> [*]What is the output of polkit-gnome-authorization when you run it from the terminal as a normal user?
** (polkit-gnome-authorization:23496): CRITICAL **: dbus_g_connection_get_connection: assertion `gconnection' failed
process 23496: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.

** (polkit-gnome-authorization:23496): CRITICAL **: dbus_g_connection_get_connection: assertion `gconnection' failed
process 23496: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
Segmentation fault

> [*]Is the HAL daemon actually running? (look for a precess called hald)
It's not, but the following is a little strange given that the daemon isn't running:

> jamyskis@jamyskis:~$ sudo /etc/init.d/hal restart
 * Restarting Hardware abstraction layer hald                       [ OK ]

> [*]Can you have a look in your logs (located in /var/log) to see if there are any pointers

Nothing much of interest, except maybe:

> Apr 28 19:39:09 jamyskis groupadd[31690]: new group: name=polkituser, GID=127
Apr 28 19:39:09 jamyskis useradd[31691]: new user: name=polkituser, UID=116, GID=127, home=/var/run/PolicyKit, shell=/bin/false
Apr 28 19:39:09 jamyskis usermod[31692]: change user `polkituser' password
Apr 28 19:39:09 jamyskis chage[31693]: changed password expiry for polkituser
Apr 28 19:39:09 jamyskis chfn[31694]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 28 19:39:09 jamyskis chfn[31694]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 28 19:39:09 jamyskis chfn[31694]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 28 19:39:09 jamyskis chfn[31694]: changed user `polkituser' information


Based on this, I've just added myself to the polkituser group. I'll get back to you on that.

> May  3 00:09:05 jamyskis kernel: [16784.056142] polkit-gnome-au[23496]: segfault at 00000010 eip 0805170d esp bfa27e80 error 4

---

### Post by chrisccoulson on 2008-05-02
Your HAL problem could be a race condition with DBUS at startup. Could you post the output of 'ls -al /etc/rc2.d'. I bet your HAL symlink has priority 12 (same as DBUS)

There is an updated hal package currently in hardy-proposed which knocks down the symlink priority for HAL to 24 (from 12) to prevent this (see [**_bug 25931_**]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931")). That should hopefully fix your HAL issue.

As for your other issues, I'll have to have a think about it in the morning, as I'm off to bed!

---

### Post by seamuso on 2008-05-02
> **chrisccoulson said:**
> Your HAL problem could be a race condition with DBUS at startup. Could you post the output of 'ls -al /etc/rc2.d'. I bet your HAL symlink has priority 12 (same as DBUS)

There is an updated hal package currently in hardy-proposed which knocks down the symlink priority for HAL to 24 (from 12) to prevent this (see [**_bug 25931_**]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931")). That should hopefully fix your HAL issue.

As for your other issues, I'll have to have a think about it in the morning, as I'm off to bed!

Thanks, this solved what I was running into with not being able to access my admin tools. bumped my HAL startup from 12 to 13 and everything unlocked the way it was supposed to.

---

### Post by chrisccoulson on 2008-05-03
Glad thats sorted it.

Has that actually fixed all your Policykit issues?

---

### Post by jamyskis on 2008-05-04
DBUS and HAL were also both set to 12 for me, so I used BUM to change the HAL priority to 14. It didn't make much of a difference, in spite of three reboots.

However, I did do a sudo /etc/init.d/dbus restart, and since then:

* Authorisations works without sudo.
* I can play movies in Totem again.
* I can start network-admin, user-admin etc. again.

Only problem that remains is that clicking the unlock button still comes up with " Could not authenticate - an unexpected error has occurred".

In any case, I'm going to wipe my hard drive and install 8.04 fresh. This laptop has been used every day for two years (it originally had 6.06 on it) and hasn't needed a reinstall. I have so much crap on here and useless config files that it's about time that I had a bit of a cleanup.

Thanks for your help, Chris!

---

### Post by LarryJ2 on 2008-05-14
Chris,
I also ran across this error and fixed it by mostly following your post.  For me the problem made itself evident when I tried to run services-admin:

> 
$sudo services-admin(services-admin:6120): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(services-admin:6120): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

** (services-admin:6120): CRITICAL **: Cannot create system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(services-admin:6120): Liboobs-CRITICAL **: oobs_session_get_platform: assertion `priv->connection != NULL' failed

The configuration could not be loaded

Based on your helpful post,  I did a ls -al /etc/rc2.d, which revealed 
...
> lrwxrwxrwx   1 root root    16 2008-04-19 18:21 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root    13 2008-05-06 07:39 S24hal -> ../init.d/hal
...
which showed the possible conflict.  Based upon your advice, I decided to try moving S24hal  to S26hal placing it after bluetooth and pulse audio.
```
~$ cd /etc/rc2.d
/etc/rc2.d$ sudo mv S24hal S26hal
``` 
That change allowed me to restart hal and dbus:
> :~$ sudo /etc/init.d/dbus restart
 * Stopping Hardware abstraction layer hald                        [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                               [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                  [ OK ] 
 * Stopping System Tools Backends system-tools-backends            [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher     [ OK ] 
 * Stopping network connection manager NetworkManager              [ OK ] 
 * Stopping system message bus dbus                                [ OK ] 
 * Starting system message bus dbus                                [ OK ] 
 * Starting network connection manager NetworkManager              [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher     [ OK ] 
 * Starting System Tools Backends system-tools-backends            [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                  [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                               [ OK ] 
 * Starting Hardware abstraction layer hald                        [ OK ] 
 

What started this mess? I was seeing error messages upon boot that flashed by asking "Is the DBus Daemon running?"  So I went System->Adminstration->Services.  There I saw that the unlock button was grayed out.  So I opened a terminal and did a sudo services-admin ( I peeked in the System->Preferences->MainMenu properties to see what was invoked to bring up the Services Settings) Since I was getting errors referencing dbus,  I attempted to remove the check mark from the "System communication bus (dbus)".  I see now it's unchecked so probably I'll have to start dbus and hal manually.  Anyway,  I made some progress, thanks to your post.

Larry

Update:  Upon reboot,  I still get the servicesAdmin.jpg Error window shown attached.  I can't connect to the internet until I open a terminal and issue: $ sudo /etc/init.d/dbus restart  Then System->Administration->Services opens (from the Gnome Menu or from sudo services-admin) but the "dBus" entry at the bottom is still without a checkmark and the unlock button is grayed out.

---

### Post by chrisccoulson on 2008-05-15
LarryJ2, the fix I posted above was to work around an identified race condition between DBUS and HAL (HAL needed DBUS running before it would start). The problem wasn't a 'conflict' as you put it. It doesn't matter if there is more than one runlevel script with the same priority as long as they aren't dependant on each other - so it doesn't matter that hal and dhcdbd have the same priority (24).

I wouldn't recommend just randomly changing runlevel script priorities in the hope of finding a solution (unless you're really really confident with what you're doing). The solution above wasn't a 'finger in the air' solution (if it was, I'd have posted a big warning).

In fact, moving the priority of HAL down to 26 is likely to cause you more issues than it solves (especially as you've bumped the priority below bluetooth and pulseaudio, as they're both likely to depend on HAL already having started I think). I would move the symlink priority for HAL back to 24, as I'm fairly certain this isn't your problem. Your problem is that DBUS isn't starting automatically when the machine boots, which is going to cause a lot of problems for lots of things.

I can't think of a solution at the moment, but I'll have a think and see if I can figure something out.

Could you have a look in /etc/init.d/rc and tell me what 'CONCURRENCY' is set to?

Could you also post the output of 'ls -l /etc/rcS.d' and 'ls -l /etc/rc2.d' and I will have a chick sanity check of your symlinks. Could you also boot without 'quiet' and 'splash' and keep an eye out for any services that fail before DBUS starts.

---

### Post by LarryJ2 on 2008-05-16
Thanks for your help, Chris.

1.  Concurrency is set to  "none"
> # Valid options are 'none' and 'shell'.
CONCURRENCY=none

2.  After I set S26hal back to S24hal,  I collected the ls -l outputs in the two files attached below.

This PC  was working just fine.   I have another HD upon which Gutsy is installed.  It works fine.   So I don't think it's a hardware problem.  

As it stands now,  I still get the "Internal error ... failed to initialize HAL!" error popup and I'm forced to issue "sudo /etc/init.d/dbus start" before I can connect to the net.  I'll look for failures in the messages that scream by after stage 1.5.

Thank fully I'm not alone in getting the HAL error message.   See [https://bugs.launchpad.net/bugs/227838](https://bugs.launchpad.net/bugs/227838)

Larry

---

