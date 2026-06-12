---
title: "Menu bar hangs when I click the clock"
date: 2008-06-11
forum: General Help
---

### Post by garton on 2008-06-11
(This is on Hardy.) Whenever I click the clock in the top right corner of the screen, the entire menubar and application bar on the bottom of the screen freezes. I have to to ctrl-alt-F1 to get a text console and restart GDM in order to get it to work again.

Any ideas on how to fix this?

---

### Post by joshsmith on 2008-06-13
i had this problem when i had evolution with a calendar (which then shows on the calendar that appears when you press the clock), but some permission thing wasnt working (it wanted to unlock the keyring but was failing)

by removing my keyrings and starting a fresh i got around this.

well, maybe this will help working out where the problem might come from at least

---

### Post by gnocci on 2008-06-20
Great!

My clock was hanging too, so i went to the keyring manager and deleted the key for my google calendar, it asked permission again and it works now.

---

### Post by garton on 2008-06-23
> **gnocci said:**
> Great!

My clock was hanging too, so i went to the keyring manager and deleted the key for my google calendar, it asked permission again and it works now.

Exactly how did you do that? I can't find anything in (what I think is) they keyring manager that deletes "google calendar key"?

---

### Post by stellarvortex on 2009-10-05
That would probably be Seahorse. I had the same problem and tried the same thing, but after entering the password again, the problem remained.

---

