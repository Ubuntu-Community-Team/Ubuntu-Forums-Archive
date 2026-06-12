---
title: "Simple one-line cat/grep script that worked on 12.04 not working on 14.04"
date: 2014-04-21
forum: General Help
---

### Post by jimwillsher on 2014-04-21
Hi all

Dead simple, one line script:

tail -f /var/log/mail.log | grep -v dovecot


On 12.04 LTS, having this in a script (/root/bin/maillog) would allow me to monitor the mail log but would exclude the lines containing "dovecot" as they were just the login/logout messages. All worked fine.

On 14.04 the same script includes all messages, including those with dovecot, so the filter isn't working. And yet, if I manually run that same simple tail | grep combination, the data is filtered correctly.

So, if I ttype

/root/bin.maillog

the data is not filtered. But if I type:

tail -f /var/log/mail.log | grep -v dovecot

the data is correctly filtered. Even though /root/bin/maillog contaisn the same commands. maillog has chmod +x and is owned by root.


Can anyone offer a solution please?

Many thanks


Jim

---

### Post by CharlesA on 2014-04-21
Use the full path to each command and see what happens.

---

### Post by jimwillsher on 2014-04-21
Many thanks forthe quick suggestion, but still no luck I'm afraid. My script now consists solely of this:

/usr/bin/tail -f /var/log/mail.log | /bin/grep -v dovecot

Running that on the command prompt works correctly. Running inside a script generates this output (for example):


Apr 21 18:45:51 heron dovecot: pop3-login: Login: user=<jim>, method=PLAIN, rip=192.168.1.210, lip=192.168.1.50, mpid=36138, TLS, session=<zg8EEpH3PADAqAHS>
Apr 21 18:45:51 heron dovecot: pop3(jim): Disconnected: Logged out top=0/0, retr=1/2355, del=0/14, size=8173674
Apr 21 18:45:51 heron dovecot: pop3-login: Login: user=<matreasurer>, method=PLAIN, rip=192.168.1.210, lip=192.168.1.50, mpid=36140, TLS, session=<y5gGEpH3PQDAqAHS>
Apr 21 18:45:51 heron dovecot: pop3(matreasurer): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0
Apr 21 18:46:04 heron dovecot: imap-login: Login: user=<jim>, method=PLAIN, rip=::1, lip=::1, mpid=36153, secured, session=<RhzJEpH3UAAAAAAAAAAAAAAAAAAAAAAB>
Apr 21 18:46:04 heron dovecot: imap(jim): Disconnected: Logged out in=506 out=1499
Apr 21 18:46:34 heron dovecot: imap-login: Login: user=<jim>, method=PLAIN, rip=::1, lip=::1, mpid=36222, secured, session=<n92UFJH3UQAAAAAAAAAAAAAAAAAAAAAB>
Apr 21 18:46:34 heron dovecot: imap(jim): Disconnected: Logged out in=506 out=1499
Apr 21 18:47:04 heron dovecot: imap-login: Login: user=<jim>, method=PLAIN, rip=::1, lip=::1, mpid=36395, secured, session=<ieRgFpH3VwAAAAAAAAAAAAAAAAAAAAAB>

so inside the script, lines containing dovecot still show.

---

### Post by jimwillsher on 2014-04-21
Sorted. I was blinkered and didn;t see "converted from DOS" at the bottom of the nano window. "flip -u" has sorted that, and it's now working.

Doh! :-)

Many thanks


Jim

---

