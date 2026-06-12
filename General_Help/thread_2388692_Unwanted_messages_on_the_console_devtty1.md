---
title: "Unwanted messages on the console /dev/tty1"
date: 2018-04-06
forum: General Help
---

### Post by Hans_van_Leeuwen on 2018-04-06
On one of our Ubuntu 16 systems, messages are logged to the console /dev/tty1.
On the console, messages appear as below:
[  OK  ] Started Session 4698 of user sysadmin
[  OK  ] Started ACPI event daemon.

The same messages (and more) are also written to the file /var/log/syslog.
On all other of our Ubuntu systems this messages are only written in the file /var/log/syslog and not to the console.

The configuration files in the directory /etc/rsyslog.d are the same on all systems.

$ ls -l /etc/rsyslog.d
-rw-r--r-- 1 root root   314 Sep  8  2015 20-ufw.conf
-rw-r--r-- 1 root root 1655 Dec  2  2015 50-default.conf

$ grep -v '^$\|^\s*\#' /etc/rsyslog.d/20-ufw.conf
:msg,contains,"[UFW " /var/log/ufw.log

$ grep -v '^$\|^\s*\#' /etc/rsyslog.d/50-default.conf
auth,authpriv.*         /var/log/auth.log
*.*;auth,authpriv.none      -/var/log/syslog
kern.*            -/var/log/kern.log
mail.*            -/var/log/mail.log
mail.err         /var/log/mail.err
news.crit         /var/log/news/news.crit
news.err         /var/log/news/news.err
news.notice         -/var/log/news/news.notice
*.emerg   :musrmsg:*
daemon.*;mail.*;\
   news.err;\
   *.=debug;*.=info;\
   *.=notice;*.=warn   |/dev/xconsole

The only difference between the system with the messages on the console
and the other systems is that the package "vault" is installed.
[https://www.archlinux.org/packages/community/x86_64/vault](https://www.archlinux.org/packages/community/x86_64/vault)

How can I stop the message logging on the console?

---

