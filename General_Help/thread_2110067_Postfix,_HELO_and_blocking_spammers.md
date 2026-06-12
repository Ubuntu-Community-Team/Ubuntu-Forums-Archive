---
title: "Postfix, HELO and blocking spammers"
date: 2013-01-29
forum: General Help
---

### Post by JackTheKnife on 2013-01-29
I'm trying to block spammers usingt the smtp_helo_restrictions controls. Additional lines to main.cf looks like

```
smtpd_delay_reject = yes
smtpd_helo_required = yes
smtpd_helo_restrictions =
          permit_mynetworks,
          check_helo_access hash:/etc/postfix/helo_access,
          permit
```

and helo_access.db file:

```
192.168.2.10   REJECT Get lost - you're lying about who you are
blabla.net     REJECT Get lost - you're lying about who you are
```

but Postfix is failin on a line 

```
smtpd_helo_restrictions = check_helo_access hash:/etc/postfix/helo_access
```

with an error info about invalid argument.

Any idea what can be wrong? 
Thanks

---

### Post by prodigy_ on 2013-01-29
There are easier and more effective ways to filter SPAM than trying to create your own anti-spam solution from scratch. If I were you I'd start here:
[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)
[http://wiki.apache.org/spamassassin/BayesInSpamAssassin](http://wiki.apache.org/spamassassin/BayesInSpamAssassin)

Spamassassin provides a lot of preset rules and and allows you modify them as you see fit. HELO related rules are also included but they are just a small part of the whole.

And one more thing: sending reject notices in reply to obvious SPAM isn't generally a wise thing to do. Spammers commonly put spoofed e-mail addresses in from/reply-to. And even when they use their actual e-mails, talking to a spambot is kind of lame. :)

---

### Post by JackTheKnife on 2013-01-29
Lets clarify this - I'm trying to block spammers which try to use my SMTP server as relay by spoofing HELO commands, not to protect users against spam (already I have installed SpamAssassin 3.3.1). Goal is to early reject any IP from the list which try to relay emails before further user authentication. As far I can see from the log SpamAssassin doesn't care about HELO.

---

### Post by prodigy_ on 2013-01-29
I see. Well, maybe you just wrote plaintext into /etc/postfix/helo_access.db as your OP suggests? That would be wrong. Postfix DB files should be created with **postmap** command.

---

### Post by jbcohen on 2013-01-29
I use thunderbird for my email and it has spam filters in it that are quite good.  Seems to me that using Thunderbird's spam filters are the simplest way to solve this problem.

I am reading threads on this forum hoping to learn a lot from forum members.

---

### Post by JackTheKnife on 2013-01-29
> **jbcohen said:**
> I use thunderbird for my email and it has spam filters in it that are quite good.  Seems to me that using Thunderbird's spam filters are the simplest way to solve this problem.

I am reading threads on this forum hoping to learn a lot from forum members.

My question is related more to the SMTP security than getting spam on email accounts  ;)

---

### Post by JackTheKnife on 2013-01-29
> **prodigy_ said:**
> I see. Well, maybe you just wrote plaintext into /etc/postfix/helo_access.db as your OP suggests? That would be wrong. Postfix DB files should be created with **postmap** command.

Good point - need to verify if helo_access.db is not a plain text :)

---

### Post by SeijiSensei on 2013-01-29
> **JackTheKnife said:**
> Lets clarify this - I'm trying to block spammers which try to use my SMTP server as relay by spoofing HELO commands, not to protect users against spam (already I have installed SpamAssassin 3.3.1). Goal is to early reject any IP from the list which try to relay emails before further user authentication. As far I can see from the log SpamAssassin doesn't care about HELO.

Is this just a performance issue?  If Postfix only accepts mail for your domain, or a set of domains, then spammers won't be able to relay mail through your server.  True the server will need to respond to HELO/EHLO, but once the remote sends an "RCPT TO" for an address outside your domain(s), the connection will be dropped.

I take an entirely different approach and run a hoary old SMTP store-and-forward daemon called smtpd on the machine that accepts inbound mail.  It allows you to specify rules based on the SMTP envelope sender, recipient address, and SMTP sending server.  You can even write a rule like:

```
deny:ALL EXCEPT *.aol.com:ALL@aol.com:ALL
```

which only accepts mail from an AOL sender that comes from its own servers.  Any traffic which passes these rules is then forwarded to a second machine running [MailScanner]("http://www.mailscanner.info/") with sendmail, ClamAV, and SpamAssassin for filtering and delivery.  I've posted the smtpd source code [tarball]("http://www.politicsbythenumbers.org/images/smtpd-2.0.tar.gz") if you'd like to take a look.

---

### Post by JackTheKnife on 2013-01-29
> **SeijiSensei said:**
> which only accepts mail from an AOL sender that comes from its own servers.  Any traffic which passes these rules is then forwarded to a second machine running [MailScanner]("http://www.mailscanner.info/") with sendmail, ClamAV, and SpamAssassin for filtering and delivery.  I've posted the smtpd source code [tarball]("http://www.politicsbythenumbers.org/images/smtpd-2.0.tar.gz") if you'd like to take a look.

Good idea but is this config worth to run for 60 email accounts? I mean time and effort spent on setting up everything + hardware.

---

### Post by SeijiSensei on 2013-01-29
Only you can answer that.  I run listservers for a couple of nonprofit organizations.  We get bombarded with spam all the time. 

You marked the thread [SOLVED].  How did you solve it?

---

