---
title: "Sending email from command line in ubuntu"
date: 2007-03-07
forum: General Help
---

### Post by k1n6 on 2007-03-07
I'm trying to get an ubuntu server install to send email from the command line. I ran aptitude and installed sendmail, but Messages I try to send dont end up getting delivered.  I am on the same network as another smtp server that I would like to relay all mail through.

Can anyone provide some quick insight as to how to easily set ubuntu up for email, or figure out where my mail conf is failing?

I'm just trying to get a script setup to send periodic emails. I know that DNS, internet, and network setting are all properly configured.  I'm using perl to send emails via the MIME::Lite plugin. Email seem to get back to my /var/mail folder with errors about being unable to route message.

---

### Post by raul_ on 2007-03-07
I never used it but i hear "mutt" is a good command-line e-mail client

---

### Post by k1n6 on 2007-03-07
By default, perl and php both are going to want to use sendmail so I guess I have a preference for getting it working.

---

### Post by k1n6 on 2007-03-07
Kinda fixed it on my own on this:::

Use the default ubuntu MTA: postfix.  I simply went into aptitude and instaled postfix.  It sets up a "sendmail" command so php and perl are happy.


I'm not sure where my sendmail cf went rock, but the postfix works outta da box.

---

### Post by dcstar on 2007-03-08
> **k1n6 said:**
> I'm trying to get an ubuntu server install to send email from the command line. I ran aptitude and installed sendmail, but Messages I try to send dont end up getting delivered.  I am on the same network as another smtp server that I would like to relay all mail through.
.........

Install the **postfix** and **mailx** packages. Modify the postfix config files to suit.

---

