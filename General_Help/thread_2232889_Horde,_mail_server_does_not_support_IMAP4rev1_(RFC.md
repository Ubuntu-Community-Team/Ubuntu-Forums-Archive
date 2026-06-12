---
title: "Horde, mail server does not support IMAP4rev1 (RFC3501)"
date: 2014-07-04
forum: General Help
---

### Post by axetone on 2014-07-04
Hi,
  I installed Horde Groupware Webmail, testing each service along the way (i.e. telnet), and everything went well UNTIL I actually loaded the webmail log-in page and received the following error:

[COLOR=#000000][FONT=Arial]**The mail server does not support IMAP4rev1 (RFC 3501).**[/FONT][/COLOR]

Any assistance / help is very much appreciated!!
 Thanks!
Server Ubuntu 12.04.4
Dovecot-imapd
Horde Groupware
Auth Admins are correct / exists in conf.php
Test.php active at:
[https://www.wildcatrockcity.com/webmail/test.php](https://www.wildcatrockcity.com/webmail/test.php)

-Axetone

---

### Post by axetone on 2014-07-05
SOLVED:
I found the solution to the IMAP4rev1 issue,...basically, after re-running "dovecot -n" I noticed that an error read:


```
doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:20: 'imaps' protocol is no longer supported. to disable non-ssl imap, use service imap-login { inet_listener imap { port=0 } }
<b>AND</b>
doveconf: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:20: 'pop3s' protocol is no longer supported. to disable non-ssl pop3, use service pop3-login { inet_listener pop3 { port=0 } }

```

So, I had to edit the dovecot.conf file and deleted the items "imaps" and "pop3s" from protocols line (leaving just imap and pop3)...below is example of what was changed;


```

protocols = imap pop3
service imap-login {
  inet_listener imap {
    port = 143
  }
}
service pop3-login {
  inet_listener pop3 {
    port = 995
  }
}

```


However, I still cannot login as now I am facing other issues...~specifically my mail.err log file (in /var/log folder) shows these new errors: 

```

Jul  5 12:54:10 mail dovecot: imap-login: Error: Timeout waiting for handshake from auth server. my pid=1684, input bytes=0
Jul  5 12:54:40 mail dovecot: auth: Fatal: No passdbs specified in configuration file. PLAIN mechanism needs one
Jul  5 12:54:40 mail dovecot: master: Error: service(auth): command startup failed, throttling

```

...~so off I go chasing those down, but at least this issue above is fixed (for now).

---

