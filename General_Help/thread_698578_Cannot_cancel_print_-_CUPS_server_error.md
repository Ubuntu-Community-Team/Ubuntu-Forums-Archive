---
title: "Cannot cancel print - CUPS server error"
date: 2008-02-16
forum: General Help
---

### Post by Man_Beach on 2008-02-16
I'm not sure why, but my wife sometimes seems to have problems printing emails.

She'll receive an few emails (we use Thunderbird) and want to print them out. Turns on the printer and  goes to file>print for each.
Nothing happens.

Checking the printer in the panel shows that the documents are 'pending'. If you try to cancel any of them you get a CUPS server error - 'error doing the CUPS operation "client-error-not-possible".

Restarting the computer clears the pending documents.

Is there any other way of clearing the pending documents? What could she be doing wrong?

We're using Gutsy and the printer is an HP Business Inkjet 1000 using the default setup.

---

### Post by nemilar on 2008-02-16
Not sure why you're getting that error, but doing

```
sudo /etc/init.d/cupsys restart
```

Will probably clear the pending documents.

---

### Post by Man_Beach on 2008-02-17
Many thanks - I'll give that a try if it happens again.

---

