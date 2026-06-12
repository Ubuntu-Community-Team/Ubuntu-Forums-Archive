---
title: "Azureus displays garbled text"
date: 2008-05-05
forum: General Help
---

### Post by akshar_patel_47 on 2008-05-05
I restarted my xserver without shutting down my azureus and when I opened azureus it told me that azureus had not shutdown properly and hence there was a problem.. I can't remember what came after that but I've attached the screenshot of what my azureus has become.

I've tried removing and installing, completly removing and reinstalling. The same garbled letters appear everytime.

Is there anyway to fix it?

---

### Post by tmetro on 2008-06-26
> **akshar_patel_47 said:**
> I restarted my xserver without shutting down my azureus...The same garbled letters appear everytime.

I ran into this same problem. I tried upgrading to 3.x, switching to a different JVM, and restarting X, but it still persisted. Eventually I ran across the setting at: Tools | Options... | Interface | Language. Apparently the abrupt shutdown had corrupted the settings file and set my language to Armenian (first choice on the list). Switching it back to Englished solved it.

I wouldn't have guessed it was an intentional language setting, as only a small portion of the UI was appearing in the unexpected font. Must be an artifact of a partial translation.

 -Tom

---

