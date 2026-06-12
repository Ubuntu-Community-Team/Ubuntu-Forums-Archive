---
title: "Open Office Won't Open"
date: 2007-03-06
forum: General Help
---

### Post by Ek0nomik on 2007-03-06
When I go to open OpenOffice.org Word Processor, I get this error:

"The application cannot be started.
An internal error occured."

Any help would be appreciated, as I want to give OpenOffice a try.  Thanks!

---

### Post by invalid on 2007-03-06
What is the output when you open it via a terminal? This may a little more helpful in tracing the problem.

---

### Post by Ek0nomik on 2007-03-06
```
fleur@fleur-laptop:~$ openoffice
[Java framework] Error in function createUserSettingsDocument (elements.cxx).javaldx failed! 
[Java framework] Error in function createUserSettingsDocument (elements.cxx).InsertFromHorizontalBitmap - empty image!

```

I look forward to some help.  It seems Java related I guess.  Something I need to install through Synaptic I imagine, but what?

Cheers!

---

### Post by Hagar Delest on 2007-03-08
Try to delete the OOo user profile ~/.openoffice.org2, OOo will create a new one.

---

### Post by Ek0nomik on 2007-03-08
> **Hagar de l'Est said:**
> Try to delete the OOo user profile ~/.openoffice.org2, OOo will create a new one.

Well that was lame.  ;)

Thanks Hagar, I appreciate it.

---

