---
title: "Evolution 2.12.0 not applying filters"
date: 2007-11-01
forum: General Help
---

### Post by devilears on 2007-11-01
Since upgrading from Kubuntu Feisty to Gutsy, i have noticed that Evolution 2.12.0 is not applying filters to new mails coming into my inbox during a session. If I shutdown Evo & start it again, the filters are applied at startup, but I have to manually apply the filters from there on. Anyone seen this?

---

### Post by richv on 2007-11-01
Yep, I have the same problem on Kubuntu after upgrading to Gusty Gibbon. Selecting the range of e-mail messages I'd like filtered and then hitting Ctrl-Y ("Apply Filters") works, but it's not an automatic thing anymore. Any clues?

---

### Post by Lerxst on 2007-12-07
I've had this problem since I upgraded to Gutsy. I Googled about this yesterday, and found something which has fixed the problem for me:
Stop Evolution and delete/rename the files ~/.evolution/mail/exchange/YOUR_ACCOUNT/personal/subfolders/Inbox/summary and summary-meta

When I started Evolution it spent at least 3 or 4 hours "filtering messages...", but all new messages **seems** to be automatically filtered now.

---

