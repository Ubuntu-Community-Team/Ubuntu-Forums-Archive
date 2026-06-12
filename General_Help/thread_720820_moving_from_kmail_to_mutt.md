---
title: "moving from kmail to mutt"
date: 2008-03-10
forum: General Help
---

### Post by spx3 on 2008-03-10
Hello,

I am recently a "fulltime" mutt user.
I like it allot.

1)
If I get my mail with mutt then I cannot get it with kmail any more.
Why is this and how can I fix it ?(I am using gmail and the emails are still
left as unread in the web interface but kmail doesn't want to get them any more).

2)
I want to achieve with it the functionality that kmail offered with its filters,
but I am not very sure how to do this.
As I understand from allot of pages in the manual this can be done through
this type of setting in ~/.muttrc
For example : 

fcc-save-hook '~t .catalyst@lists.scsys.co.uk*'     =Catalyst

As I understand the first time mutt fetches a new email that matches the regex specified
above it moves it to the directory/folder Catalyst which it creates on the fly.
Is this correct ?

I just want to do kmail behaviour in mutt.

---

### Post by andrew.46 on 2008-03-11
Hi:

> **spx3 said:**
> Hello,
I am recently a "fulltime" mutt user.
I like it allot.

Welcome to the club!

> 
If I get my mail with mutt then I cannot get it with kmail any more.
Why is this and how can I fix it ?(I am using gmail and the emails are still
left as unread in the web interface but kmail doesn't want to get them any more).


I suspect that you may have bumped into an oddity of gmail.

> 
 want to achieve with it the functionality that kmail offered with its filters,
but I am not very sure how to do this.
As I understand from allot of pages in the manual this can be done through
this type of setting in ~/.muttrc
.

If you are using pop over ssl you can achieve all the filtering you want with procmail. You did not mention if you are uing this or IMAP?

     Andrew

---

### Post by hugmenot on 2008-03-12
> **andrew.46 said:**
> I suspect that you may have bumped into an oddity of gmail.

Yeah, the Gmail oddity that you can only fetch POP mail once. Incredible, isn't it?

With an IMAP setup this does not apply. [This quick setup]("http://ubuntuforums.org/showpost.php?p=3791366&postcount=8") works well for IMAP.

---

### Post by andrew.46 on 2008-06-01
Hi:

> **hugmenot said:**
> Yeah, the Gmail oddity that you can only fetch POP mail once. Incredible, isn't it?

Not quite. The actual oddity is that gmail does *not* delete the mail from the server by default after it is read by a POP client and will leave it on the server but usually unavailable for reading again by the mail client. It can however still be browsed using the web interface.

This setting can to be manually changed at the Gmail web interface: Settings --> Forwarding and POP / IMAP --> POP Download --> 2. . When messages are accessed with POP.....

       Andrew

---

