---
title: "Evolution Inbox Problem"
date: 2007-03-07
forum: General Help
---

### Post by frantic211 on 2007-03-07
Hey All,
I have just installed a fresh version of Dapper Drake and configured evolution to connect to my works Microsoft exchange server and it seems to work OK.   My Contacts and Calendar work great, as well as all my email folders except for my inbox.  I dont have a huge amount of emails in there (about 2500), but most of the time they dont show up... When new mail comes in, it shows the number of new mails next to the inbox , but nothing is in the summary (list) window or in the message window.  It also seems that sometimes, i can copy the contents to another folder and they will show up there.  

Basically the email is coming in, but they do not show up in my inbox... nothing shows up...

Has anyone experienced this before?  Anyone have a solution?

Please Help!!!
Thanks,
Matt

---

### Post by Mr. C. on 2007-03-07
Is this using IMAP?

Microsoft email products are known to have compatibility issues with IMAP.  

Be sure your server allows enough simultaenous connections per client IP.

MrC

---

### Post by frantic211 on 2007-03-08
Hey All,
I figured out the problem.  This is what I did, I am not sure which one fixed the problem...
1.) I stripped the domain name from my login so domain\matt --> matt
2.) We have several exchange servers, and I pointed it at a different one.
3.) Changed password from plaintext to secure password
4.) Cleaned up my mail inbox (now only has about 200 emails)
5.) Killed exchange backend ```
local$ evolution --force-shutdown
```
6.) Restarted evolution

Now everything works great...Thanks,
Matt

---

### Post by Mr. C. on 2007-03-08
Good to hear.  Thanks for the update.

Best of luck,
MrC

---

