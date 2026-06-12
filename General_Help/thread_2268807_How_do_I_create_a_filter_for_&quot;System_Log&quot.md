---
title: "How do I create a filter for &quot;System Log&quot;?"
date: 2015-03-11
forum: General Help
---

### Post by greg2lapa on 2015-03-11
This used to be an easy process with 12.04. But in 14.04 it now asks for a Regular Expression?

If I want to block logs from a specific IP or a specific port, how do I set this up? Ubuntu 14.04.

---

### Post by TheFu on 2015-03-11
These are 2 different questions. Filtering on /var/log/syslog is done with some variant of grep/egrep/fgrep. These all use regex as the pattern language. There are books written about regex and you won't get too far on Unix without knowing the basics.
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) has a simple example, that is useful.
[http://regex.learncodethehardway.org/book/](http://regex.learncodethehardway.org/book/) will teach you regex - really most people only need about 20 minutes.

If you want to block IPs, use iptables and they won't get any access. There are lots of firewall front-ends to help with that.

Or am I missing the question?

---

### Post by greg2lapa on 2015-03-11
I want to set a filter so that the UFW log does not "log" a certain event. It is ridiculous to require a regular expression for this as "non technical people" do not understand regular expressions. 12.04 did not require the use of regex to set a simple log filter. Yet I can find no method in 14.04 to set a filter in System Log. Anybody know a way?

---

