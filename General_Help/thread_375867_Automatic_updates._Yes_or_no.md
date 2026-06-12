---
title: "Automatic updates. Yes or no?"
date: 2007-03-04
forum: General Help
---

### Post by bobosity on 2007-03-04
While visiting my folks I installed dapper. Mom loves it. The problem is updates. As we've seen recently sometimes an update breaks things.

While I'm here I can fix it but I'm leaving soon and won't be back for months. There is no way my mom could troubleshoot a broken system.

So what do I do? I like the idea of LTS keeping her system safe but if it gets hosed it won't work again until I return. 

Do I turn off automatic updates? That kind of defeats the point of LTS. Do I leave them on and hope that I can ssh into the machine when it breaks and fix it? If it's broken maybe it's not on the net....

I fear this is going to be a huge problem. I can just hear the first phone call...."It stopped working".

Any thoughts?

---

### Post by Spr0k3t on 2007-03-04
One question about this... if it's currently working at that point, why would you want to update it?  I'd shut down the auto-updates and only update the system when you are there.

---

### Post by Ramses de Norre on 2007-03-04
That's probably the best thing to do, yes.

---

### Post by drewbie on 2007-03-04
Why not try turning off the backports repository, should stop unnecessary updates?

I think you can set synaptic / adept to only automatically install security updates

---

### Post by Ramses de Norre on 2007-03-04
Even those are dangerous sometimes... And a simple desktop isn't really affected by the vulnerabilities addressed by those security upgrades.

---

### Post by Irony on 2007-03-04
No point in doing automatic updates - in fact I'd go to Sessions and disable update-notifier.

---

### Post by Sepero on 2007-09-11
To disable automatic download of updates:
System -> Administration -> Software Sources
Updates (tab)
heck for Updates [uncheck]
Close

---

