---
title: "Really simple MTA setup"
date: 2019-05-24
forum: General Help
---

### Post by N3d on 2019-05-24
I'm going slightly mad here. I'm looking to configure Ubuntu 18.04 server so that mail for local users is forwarded to external addresses of their choosing AND delivered into a local mailbox.

(I actually used to run a Postfix farm back in the noughties but that was a looong time ago and also feels like overkill.)

I wanted to be able to run `mail` but apparently that's part of `mailutils`, which tries to install and configure postfix as part of its installation?

Everything I've found from searching seems to about running a full MTA to act as the MX for a domain which I very much have no interest in doing ever again.

So, what's a really simple, low-effort way to get locally-generated mail delivered elsewhere? And what command can be used to test sending mail off the command line without having to install postfix?

---

### Post by TheFu on 2019-05-24
As I see it, if you want any other email server to accept the email, then you have 3 choices.
* setup individual authentications for each userid; hobbyists do this from home computers to gmail all the time. [https://help.ubuntu.com/community/EmailAlerts](https://help.ubuntu.com/community/EmailAlerts) **ssmtp** appears to work for 1 external email address. I've never used it.
* setup a proper email server/gateway on a static, non-residential, IP range, and use MX, SPF and DMARC records; the free Amazon tiny server should be able to handle this load. The DNS records are necessary only if you don't want your emails rejected by normal email servers.
* pay an email relay service to accept mail from your system; dyn used to do this for $20/yr. I don't know if they still do. I used it for a few months a decade ago and it worked.  Sending email and receiving email are sold separately.

I install postfix on all my systems as a "satellite" system. Each can only send email to a relay host (my main "real" email server) and I'm careful to have local aliases forward to real accounts on the main domain.  This is mainly so I get daily systems reports, but also so I can quickly throw an email anywhere from a shell with addresses that won't accept replies. ;)

I think only the 2nd option actually requires having a domain. The others require using credentials.

I'm interested in what you find, especially if it is something else.

---

### Post by SeijiSensei on 2019-05-24
I'd use sendmail+procmail for this task. Sendmail will deliver the mail into /var/spool/mail/username.  You can drop a .procmailrc in /home/username that will duplicate the message and forward the copy to another mailbox while delivering the first copy locally.

```

# make a copy of every message and forward it to me@example.com
:0c
! me@example.com

```

You're not going to be able to avoid using an MTA for this.

You can install the "mail" program from the package bsd_mailx.  It works with sendmail.

[https://launchpad.net/ubuntu/bionic/+package/bsd-mailx](https://launchpad.net/ubuntu/bionic/+package/bsd-mailx)

---

### Post by N3d on 2019-05-24
Ahhhh, thanks for the heads up on bsd_mailx!

---

### Post by N3d on 2019-05-24
ssmtp look interesting!

---

### Post by HermanAB on 2019-05-24
I used nullmailer in the past.  Super simple.  

There are a few others that are similar.

---

### Post by N3d on 2019-05-25
If anyone's interested, I just went ahead and configured Postfix. It did feel like overkill to begin with but it's really not that bad, and for me it had the major advantage that I already knew it pretty well. I typed up my notes mainly for myself but maybe someone else can benefit:

[https://gist.github.com/n3dst4/1ce07bd0ef11fa180c630197ead45624](https://gist.github.com/n3dst4/1ce07bd0ef11fa180c630197ead45624)

---

### Post by SeijiSensei on 2019-05-25
I'm pretty sure procmail will work with Postfix as well as sendmail.

---

### Post by TheFu on 2019-05-25
> **SeijiSensei said:**
> I'm pretty sure procmail will work with Postfix as well as sendmail.

Yep.  100% certain that postfix and procmail work together.  I'd be surprised if Exim didn't too, but those guys do things a little too differently for my comfort. ;)

---

