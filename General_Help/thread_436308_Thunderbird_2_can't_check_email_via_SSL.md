---
title: "Thunderbird 2 can't check email via SSL"
date: 2007-05-07
forum: General Help
---

### Post by Tickle Me Elmo on 2007-05-07
Hello,


I'm having trouble to get thunderbird to both check emails and do other tasks, such as to subscribe to mailboxes over SSL.

It works fine over regular IMAP and from a pc within the LAN (NAT) running windows it works fine too, so I don't think it's a firewall issue.


Anyone knows what to do about this? I'm confused... :confused:

---

### Post by Tickle Me Elmo on 2007-05-08
I'd like to add that I installed Thunderbird 2 via Automatix. I have open-ssl installed, if that should make any difference (I can surf to sites using https via Firefox 2)

If anyone know about this problem, please advice. I'd be most grateful!

---

### Post by TransitMan on 2007-05-08
Are you using a POP email address?
If so, you need to put the POP server information in, then check the box labeled SSL.
I am still on 1.5.11 and can connect with SBCGlobal.net via SSL just fine. 
No open SSL required.

---

### Post by Tickle Me Elmo on 2007-05-08
I am on IMAPs, and I have found out what was causing it by looking in "messages" in Thunderbird 2 (I haven't seen this field in the windows version, or I missed it.

What was messing up the TB2-installment was the add-on "remember mismatched domains" - it has to be re-installed after migrating to another machine as I gather it.

So, if anyone has issues similar to what I had - do the above.


Cheers! :)

---

