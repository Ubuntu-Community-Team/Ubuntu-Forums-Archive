---
title: "[SOLVED] Multiple Entries in /var/log/mail.log"
date: 2007-10-17
forum: General Help
---

### Post by btaylor101 on 2007-10-17
I was curious as to why the mail log has 4 entries for the same event. The example is listed below, but sometimes I see two and others 4 lines. I get the point for two lines, one for logging in and the other for logging out, just not the duplicate entry.

> Oct 17 08:01:09 BigBoss dovecot: imap-login: Login: user=<btaylor101>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 17 08:01:09 BigBoss dovecot: IMAP(btaylor101): Disconnected: Logged out
Oct 17 08:01:09 BigBoss dovecot: imap-login: Login: user=<btaylor101>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 17 08:01:09 BigBoss dovecot: IMAP(btaylor101): Disconnected: Logged out
Oct 17 08:01:09 BigBoss dovecot: imap-login: Login: user=<btaylor101>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 17 08:01:09 BigBoss dovecot: IMAP(btaylor101): Disconnected: Logged out

---

### Post by kidders on 2007-10-18
Hi there,

Although it's certainly *possible*, I doubt very much that these log entries are duplicates. It's more likely that your mail client is simply opening and closing multiple IMAP connections in rapid succession (ie all within one second of each other). In other words, I'd say your logs are simply reflecting what your server is doing, which is what they are designed to do.

I suppose, if you're really concerned, you could verify my suspicion by monitoring TCP connections at the IMAP server, but I'd be surprised if you discovered anything unexpected.

---

### Post by btaylor101 on 2007-10-19
Thank you for the information. Just wanted to make sure something wasn't awry.

---

### Post by kidders on 2007-10-19
No worries.

If you continue to be bothered by all the repeated messages, you could try reducing dovecot's log verbosity (if it will go any lower!) or increasing your log rotation frequency. Either should keep your mail log files nice and small.

You've no reason to worry though ... the log entries you posted seem quite normal.

All the best.

---

