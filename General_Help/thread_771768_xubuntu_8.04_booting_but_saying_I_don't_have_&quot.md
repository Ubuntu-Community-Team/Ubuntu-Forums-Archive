---
title: "xubuntu 8.04 booting but saying I don't have &quot;priveledges&quot; so I can't add software"
date: 2008-04-27
forum: General Help
---

### Post by emergingtechnologies on 2008-04-27
Just installed Xubuntu 8.04 and I log in but it tells me it's booting without priveledges which means I can't use the package manager.  I need to set this system up for an elementary school teacher by tomorrow morning -- could someone please help?

---

### Post by ryanhaigh on 2008-04-27
I think you need to clarify on exactly what the error message is and when you get it. You say you log in but your getting an error message about booting? It sounds more like you are trying to run synaptic or another admin program after you have logged in.

---

### Post by rubicon on 2008-04-27
First, have you actually tried to install something? What it says?

Then show us ```
groups <your_username>
```

---

### Post by emergingtechnologies on 2008-04-27
Sorry for the poorly worded question.  I did not know how to get Administrative Privileges on my new Xubuntu install -- apparently it now defaults to a non-administrative account that cannot use Synaptice Package Manager.

Anyway... I continued digging and found my answers here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks all.

---

