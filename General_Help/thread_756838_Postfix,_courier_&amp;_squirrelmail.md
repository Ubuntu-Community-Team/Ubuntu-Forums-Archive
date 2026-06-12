---
title: "Postfix, courier &amp; squirrelmail"
date: 2008-04-16
forum: General Help
---

### Post by dchurch24 on 2008-04-16
Hi all,

I'm trying to set up my mailserver, but am having nothing but trouble at every step.

I installed postfix and courier as per the following guide:

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p5](http://www.howtoforge.com/perfect_server_ubuntu7.10_p5)

I have managed to sort out the problem with not having a Maildir created etc...and can now send mail via, either telnetting into port 25 and doing it manually or by using the squirrelmail setup to send.

Sending is no problem.

Receiving is.

To start with mail was just being refused:

```

 You do not have permission to send to this recipient.  For assistance, contact your system administrator.

```

I added this to the /etc/postfix/main.cf file:

```

mynetworks = 127.0.0.0/8, xx.xx.xx.xx/28    (xx = my external IP)

```

...and then it no longer bounces back, but the emails never arrive, at least not in the squirrelmail.

I thought I would telnet to port 143 and check, but once there anything I type (login, etc...)

returns:

```

NO Error in IMAP command received by server.

```

I have searched everywhere for this, and the answer is either left like that, or ends with someone saying, "You don't want to use [courier][postfix][squirrelmail][etc...], you want to use this [insert users favourite mail server software here].

I'm sure this is just something daft, like I haven't set up a user or something (I have set up a linux user, and that seems to let me into the mailbox using squirrelmail, so I assume that it's set up ok?).

Can anyone point me in the right direction?

I'm getting rather desperate now, and after trawling through about 40 pages of google links and about 40 here, I am at my wits end! ;-)

---

### Post by dchurch24 on 2008-04-16
Ok, I finally got it.

I completely uninstalled everything (apt-get remove --purge) and reinstalled it.

One thing though, I found that there would be errors in Squirrelmail, that is until the user receives their first mail - it then seems to set up the folders that it needs, but not before.

---

