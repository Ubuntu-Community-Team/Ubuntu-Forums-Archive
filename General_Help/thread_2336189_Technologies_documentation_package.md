---
title: "Technologies documentation package?"
date: 2016-09-05
forum: General Help
---

### Post by tim.rohrer on 2016-09-05
Hello--

I have been using Linux for years in limited roles for years, so while I am comfortable poking around (I'm more experienced with OS X), I still need to RTFM when I go to set up new Linux servers.
 
My latest project is to build a monitoring server, which I've started doing so with 16.04 using a basic server install plus the OpenSSH package. Manually configured the /etc/network/interfaces, no problem, but then I came to the first issue: how to restart the network service. Not able to recall exactly the structure of the ***service ***command I turned to Google and found a couple references (eg. [https://linuxconfig.org/how-to-restart-network-on-ubuntu-16-04-xenial-xerus-linux](https://linuxconfig.org/how-to-restart-network-on-ubuntu-16-04-xenial-xerus-linux)) that indicated I should issue ***sudo systemctl restart NetworkManager.service***, which on my box gave me an error stating the unit was not found. The next option on the list failed too with the same error, and so I realized I can use ***sudo service networking restart ***and it seemed to work.

Next I found someone's notes on how to configure syslogd on a 12.04 server to receive messages from various clients. The example rsyslog.conf he used contains different command formats than are in the file on my server, and while I figured some of them out, I decided I needed to do more research to understand the others. RSYLOG.CONF(5) indicates there is extensive HTML documentation but that it might be in a different package. The comments in the /etc/rsyslog.conf file even provide a path to rsyslog_conf.html which I do not have on my system.
 
I found the packages.ubuntu.com site and searched in Documentation and more broadly for rsyslog_conf.html, without any luck. I guess my next step will be to go find the homepage for rsyslog and try and determine what has changed in the development. And, of course, read through the man pages is earnest. 

My questions:
[LIST=1]
[*]Am I missing something on my system that should install these missing documents under /usr/share?
[*]Does the community have other documentation covering the technologies found in the 16.04 release and how they have changed since the 14.04 and previous releases?
[/LIST]

Thanks.
Tim

---

### Post by TheFu on 2016-09-05
16.04 switched to systemd.  Logging is completely different under systemd - and should be easier to do remote logging than before from the systemd training I've had. So are starting/stopping services, though, in theory, everything is backwards compatible.

BTW, don't confuse "desktop" instructions with "server" instructions.  Don't think network manager has anything to do with server installs. At least I've never seen it on an of mine.

There is a "Server Guide" - google will find it easily. You might find that helpful, but I'm unsure what you mean by "documentation package."  Every command should have a manpage and there are ways to search all the manpages ... oddly, **man man** will explain. ;)

The big changes between releases will be outlined in the release notes and change log. Don't know if they address LTS-->LTS changes.  Since I'm active here, I usually read about the big changes coming (systemd) months in advance, then complain about stupid changes for no good reason (systemd is a solution trying to solve a problem I don't have and introducing more problems along the way ... imho).

/usr/share/   ... .don't really use that much. It usually has example config files for complex daemons, IME. It is the last place I look. Perhaps I should use it more?

---

