---
title: "Fetchmail - Small Mail Server"
date: 2007-10-28
forum: General Help
---

### Post by terciof on 2007-10-28
Hi All!!

Here we have a company that do our Web Hosting and Mail Hosting(MX).

We access our email from them by POP3.

We need to fetch our emails(about 50 accounts) from that remote POP3 server, and provide a local IMAP server to those accounts...

What is the best choice??

I don't need MTA, SMTP will be provided by our Hoster.

I'm thinking using courier and fetchmail... will it work?? What about account names?

Thanks!

Tercio.

---

### Post by mannih2001 on 2007-10-31
Fetchmail an courier should work just fine, but you will also have to install some smtp software such as postfix because (AFAIK) that's the only way that fetchmail will be able to deliver the fetched emails locally.

The real problem with what you are trying to achieve is that your fetchmail scripts will need to know the passwords of your users. You will have to setup users on your server (preferably with the same login names they have with your hosting company). This is going to be a mess to maintain and your users will have a hard time changing their passwords). 

Finding a hosting company that let's you do IMAP should be a lot easier and cheaper.

---

### Post by terciof on 2007-10-31
Hi mannih2001,

About the passwords, it's not a problem, because we have tracking about users passwords, and we change it every 2 mounths, but we have some scripts to do that!

About a hosting with IMAP, our hosting company already have that, but our needed is to store a lot of emails, about 6gb each account.... 

So we need a local solution.... :-(

Thanks!

---

