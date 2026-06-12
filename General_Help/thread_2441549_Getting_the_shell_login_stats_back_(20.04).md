---
title: "Getting the shell login stats back (20.04)"
date: 2020-04-24
forum: General Help
---

### Post by msikma on 2020-04-24
Hi all. I've just installed Ubuntu 20.04 on a new server. When I first logged in, I saw the following data:

```
Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.4.0-26-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Fri 24 Apr 2020 01:45:51 PM UTC

  System load:           0.0
  Usage of /:            8.1% of 24.06GB
  Memory usage:          16%
  Swap usage:            0%
  Processes:             106
  Users logged in:       1
  IPv4 address for eth0: [ip address]
  IPv4 address for eth0: [ip address]
  IPv6 address for eth0: [ipv6 address]


1 update can be installed immediately.
0 of these updates are security updates.
To see these additional updates run: apt list --upgradable

```

I've since installed Fish Shell and a different user, and now I don't see this message anymore. I'm wondering, where's the code that generates this welcome screen?
I'd like to get some of these stats back. Like the list of available updates and system stats are very useful, so I'd like to program my Fish Shell to show these.
Thanks!

---

### Post by deadflowr on 2020-04-24
it's motd (message of the day)
[https://linuxconfig.org/how-to-change-welcome-message-motd-on-ubuntu-18-04-server]("https://linuxconfig.org/how-to-change-welcome-message-motd-on-ubuntu-18-04-server")
[http://manpages.ubuntu.com/manpages/bionic/man5/update-motd.5.html]("http://manpages.ubuntu.com/manpages/bionic/man5/update-motd.5.html")

---

### Post by msikma on 2020-04-24
Thanks. I found that the source for these messages is in ```
/etc/update-motd.d/
```.

For my needs I can see that the system info is mostly controlled by ```
cat /var/lib/update-notifier/updates-available
``` for the updates, and the ```
landscape-sysinfo
``` program.

---

