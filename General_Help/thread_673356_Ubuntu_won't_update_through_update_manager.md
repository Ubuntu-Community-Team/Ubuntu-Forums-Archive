---
title: "Ubuntu won't update through update manager"
date: 2008-01-20
forum: General Help
---

### Post by Lord Xeb on 2008-01-20
When I go to updated, it says that it downloaded 6 files, but none of them install.... help?

---

### Post by steveneddy on 2008-01-20
sudo apt-get update
sudo apt-get upgrade


Are there any error messages?

---

### Post by Lord Xeb on 2008-01-20
I don't think there are but I will put a screen shot in just encase

---

### Post by oldb0y on 2008-01-20
Try updating your repos. System>Administration>Synaptic>Settings>Repos, tick of all on the first page, and let Synaptic update.

---

### Post by Lord Xeb on 2008-01-20
when I do updates though update manager, it says downloading 6 packages but then when it finished, nothing happens

---

### Post by oldb0y on 2008-01-20
Well, is your system out-of-date? Do you need to update it?

---

### Post by steveneddy on 2008-01-20
> **Lord Xeb said:**
> I don't think there are but I will put a screen shot in just encase

Looks OK from here.

What it is DLing is the snapshot of the repos to see if you need an upgrade.

---

### Post by Lord Xeb on 2008-01-20
thanks that worked.... (there were 173 updates)

---

