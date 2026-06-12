---
title: "Sending mail"
date: 2008-03-13
forum: General Help
---

### Post by vanderkerkoff on 2008-03-13
Hello everyone

I've just installed ubuntu 7.10 and I haven't installed any further mail software.

When I try to send mail from the command line like so

mail [email]email@adress.co.uk[/email]
Subject: Hello
hello
Cc: 


It bounces back from the remote mta server that I'm trying to send mail to, that is supposed to happen as I haven't told my MTA to accept incoming mail from this server yet.

My question though is this, it's currenlty trying to send mail from username@machinename

I'll need to change that to be an email address that my remote MTA will allow.

Is there an easy way to change the default from mail?

I'm not sure what is trying to send that mail, any ideas or hints will be extremely helpful.

Thanks

---

### Post by kyphi on 2008-03-13
You still need an email programme.

Why not use Mutt?  (type "mutt" in a terminal)

---

### Post by vanderkerkoff on 2008-03-14
Hi Kyphi

It turned out that postfix was on the pchine so I configured that.

Plus it was kind of an idiotic quetion in part, as you set the From address in the form code of the website.

I keep forgetting that, but I'll try to remember this time now I have publicly humiliated myself again.

:-0

---

