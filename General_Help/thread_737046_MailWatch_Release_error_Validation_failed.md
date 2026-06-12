---
title: "MailWatch Release error Validation failed"
date: 2008-03-27
forum: General Help
---

### Post by sachem_s on 2008-03-27
Hi 
This has been bugging me for long now and after hours of googling and searching the forums I had to finally post this question,
My server runs MailScanner and Mailwatch as a spam filter, everything was working fine until ORDB suddenly blacklisted all mails as spam, this took me a couple of hours to figure out, by the time i had fixed this I had well over 500 mails tagged as spam and moved to the quarantine section. I have tried to release them individually but I keep getting this error "Release: error (Validation failed for spam filter)". 
Hoping someone can help me with this.
I tried to run sendmail from the command line, but the command just sits there and does nothing, am I doing something wrong. Please help. :(

Sachem

---

### Post by sachem_s on 2008-03-30
Managed to fix is through the command line using sendmail
  tried sendmail -t -i < message_id

however I wish there were an eaisier way to do this as I had over 500 messages to release, it took quite a while.

Sachem.

---

