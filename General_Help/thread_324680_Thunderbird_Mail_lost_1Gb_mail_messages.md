---
title: "Thunderbird Mail lost 1Gb mail messages"
date: 2006-12-24
forum: General Help
---

### Post by Dutch on 2006-12-24
Hi,

Thunderbird Versie 1.5.0.7 (20060922) handels my E-mail
Alright that's nice U may think :-)

Ok, last week I saw after beeing away from my PC for 5 minutes that I've got 143 new E-mails within 5 minutes and counting.
When I looked at the content of the mails it were old mails and Thunderbird started with bringing them at top of the IN Box and also thhey were Bold like new mails.

When I've got 300+new mails (It were stil old mails presented as new) I had enough of it and I closed downd Thunderbird.

Here's the nice thing: when I restarted Thunderbird My Inbox was completely empty ! Have a nice Xmas !
My Ubuntu is 2.215.27.686 I have a 80 Gb HD with 17 Gb left free.
P IV And I have /home seperate.


Are my e-mails gone to the next level ?
Please some help with refinding those, and what hapened ? 

Thanks,

Paul.

---

### Post by Jussi Kukkonen on 2006-12-24
The mail files are in ~/.mozilla-thunderbird/<profiledir>/Mail, in my case */home/jku/.mozilla-thunderbird/bmmnv2x6.default/Mail/*. You should be able to locate your "Inbox" file somewhere there (there may be several inboxes if you have several mail accounts), If the file is there the  mails should be intact (you can try reading it with a text editor).

I'd try creating a new profile in Thunderbird (*mozilla-thunderbird --ProfileManager*) and importing your old Inbox into that new profile.

---

### Post by Dutch on 2006-12-24
> **Jussi Kukkonen said:**
> The mail files are in ~/.mozilla-thunderbird/<profiledir>/Mail, in my case */home/jku/.mozilla-thunderbird/bmmnv2x6.default/Mail/*. You should be able to locate your "Inbox" file somewhere there (there may be several inboxes if you have several mail accounts), If the file is there the  mails should be intact (you can try reading it with a text editor).

I'd try creating a new profile in Thunderbird (*mozilla-thunderbird --ProfileManager*) and importing your old Inbox into that new profile.

Thanks Jussie.
This is my folder:

paulaccount/.mozilla-thunderbird/wyb2mtdh.default/Mail/Inbox.sbd/

In the Inbox.sbd I see al my old subfolders (who have al the content) but the IN Postbox I cant see no where !

---

### Post by Jussi Kukkonen on 2006-12-25
the actual  Inbox file (without any postfix) should be in the same dir as Inbox.sdb.

---

### Post by Dutch on 2006-12-25
> **Jussi Kukkonen said:**
> the actual  Inbox file (without any postfix) should be in the same dir as Inbox.sdb.

When I look for "Inbox.sdb" I get nothing in return.
I read something about that the messages coukd be there butthat Mozilla made them invisible ?

---

