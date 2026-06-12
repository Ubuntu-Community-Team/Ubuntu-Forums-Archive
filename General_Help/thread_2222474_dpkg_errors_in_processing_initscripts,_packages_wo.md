---
title: "dpkg errors in processing initscripts, packages won't configure or install"
date: 2014-05-06
forum: General Help
---

### Post by sam52 on 2014-05-06
Hi all,

I operate my own website and have recently migrated the whole operation over to my own private server. I wanted more control over the website and in general a better understanding of everything that happened behind the scenes as I went along. All has been going slightly choppy in coming to terms with Ubuntu, however I've hit a roadblock when it's come to setting up mail services. I discovered that PHP email wasn't actually working, so I set about installing packages that I thought would help out. However in doing so something went wrong, not quite sure what (attempted postfix install), and now no packages install. There's error messages relating to **dpkg: error processing package initscripts (--configure):** and a whole lot else I don't quite understand yet. I've been scowering the net for help all day, yet none of the proposed solutions do anything for me nor help inform me of what the actual issue is. Any assistiance fixing the following would help as I'd like to get back on track to installing a mailservice (sendmail, postfix etc related) so I can enable PHP Emails from my wordpress site.

```
Setting up initscripts (2.88dsf-53) ...
insserv: warning: script 'firewall' missing LSB tags and overrides
insserv: There is a loop between service monit and firewall if stopped
insserv:  loop involving service firewall at depth 2
insserv:  loop involving service monit at depth 1
insserv: Stopping firewall depends on monit and therefore on system facility `$all' which can not be true!
insserv: warning: script 'firewall' missing LSB tags and overrides
insserv: There is a loop between service monit and firewall if stopped
insserv:  loop involving service firewall at depth 2
insserv:  loop involving service monit at depth 1
insserv: Stopping firewall depends on monit and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package initscripts (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initscripts
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
Errors were encountered while processing:
 initscripts
 dbus
 udev
 consolekit
 x11-common
 libice6:amd64
 libsane:amd64
 libsm6:amd64
 libxt6:amd64
 libwebkitgtk-3.0-0:amd64
 libxtst6:amd64
 ifupdown
 at-spi2-core
 policykit-1
 colord
 libyelp0
 yelp
 gnome-user-guide
 sane-utils
 zenity
```

---

### Post by ian-weisser on 2014-05-09
> **sam52 said:**
> Setting up initscripts (2.88dsf-53) ...


That's a nonstandard version of initscripts. 14.04 and 14.10 use 2.88dsf-41
So you got it from someplace other than Ubuntu. That's important. It means you have discovered a bug that should be reported directly to the upstream developers (not to Ubuntu). You can also work around the problem by using an older version of the package that lacks the bug.

> **sam52 said:**
> 
insserv: warning: script 'firewall' missing LSB tags and overrides
insserv: There is a loop between service monit and firewall if stopped
insserv:  loop involving service firewall at depth 2
insserv:  loop involving service monit at depth 1
insserv: Stopping firewall depends on monit and therefore on system facility `$all' which can not be true!


That's the detail of the problem. The file /etc/init.d/firewall is malformed, and has an improper relationship with another service that causes a loop under some conditions (that's bad).

> **sam52 said:**
> 
dpkg: error processing package initscripts (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initscripts
E: Sub-process /usr/bin/dpkg returned an error code (1)

That's dpkg reporting that it couldn't install initscripts because of the problem.

---

