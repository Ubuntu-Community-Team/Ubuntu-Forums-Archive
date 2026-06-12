---
title: "Pine and MSMTP"
date: 2007-09-19
forum: General Help
---

### Post by axrh on 2007-09-19
Hi Guys,

I'm trying to set up msmtp with pine.  I have two accounts on pine, so how can I get msmtp to send to the from: address that is set in pine?

Thanks!

---

### Post by andrew.46 on 2008-02-12
Hi,

 I use msmtp with mutt and what you ask should not be a problem. The man pages for msmtp give an example of two accounts with global settings at the beginning:

> # Set default values for all following accounts.
       defaults
       tls on
       tls_trust_file /etc/ssl/certs/ca-certificates.crt
       logfile ~/.msmtp.log

       # A freemail service
       account freemail
       host smtp.freemail.example
       from [email]joe_smith@freemail.exam[/email]ple
       auth on
       user joe.smith
       password secret

       # A second mail address at the same freemail service
       account freemail2 : freemail
       from [email]joey@freemail.exam[/email]ple

Should be easy enough to setup your 2 accounts as above?

                   Andrew

---

