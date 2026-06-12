---
title: "Anybody here clever with postfix? (or another email daemon)"
date: 2008-07-02
forum: General Help
---

### Post by MikeDX on 2008-07-02
Dear all

I'm trying to setup a system where all my emails get put into a mysql database, and am under the impressiong that postfix will do this for me.

So far I have  fetchmail grabbing emails out of my various pop3 accounts, and shoving them into my local postfix server (firewalled, behind private ip, blah blah blah).

I understand you can get postfix to process emails as they are delivered locally, before it shunts them into a users mailbox. 

Anybody out there with a little postfix knowledge care to share some info, or even how I can achieve the same result by other means?

Ultimately I want to put emails into different databases/tables (or even no database at all) based on different criteria (sender,subject, size).

Thanks in advance!

Mike

---

### Post by HermanAB on 2008-07-02
Nope, Postfix doesn't do that.

Citadel is the only Linux mail system I know of that uses a database backend (BerkeleyDB).  It can handle hundreds of Terabytes of email and will only save a single copy of a message when addressed to multiple users.

[http://citadel.org](http://citadel.org)

Cheers,

Herman

---

### Post by MikeDX on 2008-07-02
> **HermanAB said:**
> Nope, Postfix doesn't do that.

Citadel is the only Linux mail system I know of that uses a database backend (BerkeleyDB).  It can handle hundreds of Terabytes of email and will only save a single copy of a message when addressed to multiple users.

[http://citadel.org](http://citadel.org)

Cheers,

Herman

Interesting.  A company I used to work for used postfix to process their incoming mail, and then processed it through something like an "agent" (not sure of the nam, delivery agent maybe) to do whatever you wanted with it. The database part is a bit of a red herring in that I dont want postfix to talk directly to mysql (or any particular database) thats just the end result.

Also, its worth knowing that I just want postfix to handle the incoming mail, once it has been processed I have no interest in talking to postfix directly to access those emails, in fact no email client will be talking to it at all.

---

