---
title: "System mail forwarding"
date: 2012-12-05
forum: General Help
---

### Post by J Blain on 2012-12-05
Hello,

I have a laptop computer running Ubuntu 12.10 64 bits. I use this machine at work (corporate network).

---- My /etc/hostname   contains

Lenovo-ThinkPad-T400

---- My /etc/hosts      contains

127.0.0.1       localhost
127.0.1.1       Lenovo-ThinkPad-T400

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---- My /etc/aliases  contains

webuser: root
root: [email]myemail@gmail.com[/email]
jblain: [email]myemail@gmail.com[/email]

Now here is my problem, if I send an email to my gmail address directly

$php -a
$mail('myemail@gmail.com','GMAILTEST','WORKING?!?');

This works perfectly and I immediately see the email arrive in my gmail Inbox. But if I send to eitheir jblain or root,
the email seems to disappear, instead of getting to gmail because of the aliases.

Any suggestions anyone ?

Regards

Jacques Blain

---

### Post by SeijiSensei on 2012-12-05
What do you see in /var/log/mail.log?  That's always the first place to look if you need to debug mail problems.

I assume you have Postfix or some other SMTP server like sendmail installed, yes?

---

### Post by aromo on 2012-12-05
> **J Blain said:**
> $php -a
$mail('myemail@gmail.com','GMAILTEST','WORKING?!?');

This works perfectly and I immediately see the email arrive in my gmail Inbox.

This means your mail routing part is fine.

> **J Blain said:**
> But if I send to eitheir jblain or root,
the email seems to disappear, instead of getting to gmail because of the aliases.


This seems like you are having issues with your aliasing.  Have you run ```
newaliases
``` ?

---

