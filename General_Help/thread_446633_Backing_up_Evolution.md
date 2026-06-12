---
title: "Backing up Evolution"
date: 2007-05-17
forum: General Help
---

### Post by Damo1976 on 2007-05-17
Hello again.

I am using a dual boot laptop at the moment whilst I was trying out Ubuntu.
I have decided now that I love it and wish to make my machine Ubuntu only.
I am intending on formating everything (2 x 100MB Drives) and sticking Feisty on a clean system.
However, I have also decided that I don't like Evolution.

Should I use wine/cross over to put Outlook on there, or a VM instead and run XP Pro in a different screen.
I also want to be able to use Office, and the various Nokia bits of software which all work nicely with Outlook.

So, other than the question above, I would like to know how I migrate back away from Evolution?  

Any other advice on my impending project would also be gratefully accepted.

Please help.

Damian

---

### Post by judoka9999 on 2007-05-17
Hello,

I'm not an evolution fan either. I find even w/ exchange as an email server I'd rather use thunderbird (an email client from the mozilla project) w/ IMAP. I'm not sure if you've considered thunderbird, but I'd recommend it.
If you need compatability with windows programs then I would say yes, grab a copy of VMWare Workstation and use a VM. There is a vmware patch you must use to get either vmware workstation or server to install properly on Ubuntu. However, once installed, if your Nokia device connects via USB you should be able to get it to work.
In terms of migrating away from evolution, what type of email server do you have?
If you use exchange, then its probably as simple as configuring the new client. If you have messages configured to be removed from the exchange server you can just disable that setting and push them back to your mailbox on the exchange server.
If your not using exchange, see if your email server supports IMAP. If IMAP is the case, then again check your config and see if you are actually pulling the messages off the server, or if they are remaining there. If you have been pulling them off, then you can just push them back via IMAP. One quick way to know if you are using IMAP or POP3 is, do you use public folders? If you use public folders and know you're not on exchange, you can be reasonably sure you are using IMAP.
If you are using POP3 and have no IMAP access, then things will get a bit trickier. Let me know if this is the case, and I'll try to figure something out for you.

--Judoka

---

### Post by Damo1976 on 2007-05-17
Hi 

Thanks for the reply.
I'm using POP and I don't even know what IMAP is.
I'm a single user, and don't have a special set up.

I've tried Thunderbird in the past, and its fine for email, but I like to use the contacts and diary functionality - and I like it to sync with my mobile phone. 

With Outlook for instance, it is very simple to copy the pst file from one location to, say, an external drive, then put it back when you've finished messing around with the computer - for example when shifting everything to a new one. 
This is essentially what I want to do, as I need to clean my hard drive completely and start afresh.

Thanks in advance.

---

