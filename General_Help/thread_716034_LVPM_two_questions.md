---
title: "LVPM two questions"
date: 2008-03-05
forum: General Help
---

### Post by Feivel on 2008-03-05
This morning I downloaded the newest LVPM from sourceforge with the idea of resizing my virtual disk. I ran LVPM and chose to resize to 20 gig but I was too chicken to reboot into windows and rename new.disk to root.disk (after renaming root.disk first). Since I am running Hardy Heron there is a chance with each update that I will break my installation so I was wondering if I keep a copy of new.disk in another directory, isn't that a full backup of my Ubuntu install? Also if I rename new.disk to root.disk and Ubuntu doesn't boot, can I just rename the original root.disk and will everything be fine? The only reason I ask is I am VERY familiar with the way Windows follows Murphy's law.

---

### Post by ago on 2008-03-05
I see no problem in renaming 

root.disk  -> root.disk.backup
new.disk -> root.disk
root.disk.backup -> root.disk #if things go sour

---

### Post by Feivel on 2008-03-05
> **ago said:**
> I see no problem in renaming 

root.disk  -> root.disk.backup
new.disk -> root.disk
root.disk.backup -> root.disk #if things go sourJust what I thought. Just checking before I hose my install. Eventually I will resize my partition so I can dump Vista or would it be easier to do a full backup (to a different disk) and reinstall Hardy Heron fresh?

---

### Post by ago on 2008-03-05
> **Feivel said:**
> Just what I thought. Just checking before I hose my install. Eventually I will resize my partition so I can dump Vista or would it be easier to do a full backup (to a different disk) and reinstall Hardy Heron fresh?

I would opt for a fresh installation after final, you can use wubi before that and upgrade from time to time. The ubuntu installer will resize the partitions for you, no need to do that in advance.

---

### Post by Feivel on 2008-03-05
> **ago said:**
> I would opt for a fresh installation after final, you can use wubi before that and upgrade from time to time. The ubuntu installer will resize the partitions for you, no need to do that in advance.

So i can just keep new.disk as a full backup just in case. then as soon as HH goes final I will just do a fresh install on a NEW HD that never saw windows :)

---

### Post by ago on 2008-03-05
> **Feivel said:**
> So i can just keep new.disk as a full backup just in case. then as soon as HH goes final I will just do a fresh install on a NEW HD that never saw windows :)

Or you can make some space on the same drive where you have Windows without buying a new one... Ubuntu installer will do that too if you wish.

---

### Post by Feivel on 2008-03-05
> **ago said:**
> Or you can make some space on the same drive where you have Windows without buying a new one... Ubuntu installer will do that too if you wish.

Buy? Never going to have to buy a HD for the rest of my life. Still got a 320 gig SATA in the box.

---

