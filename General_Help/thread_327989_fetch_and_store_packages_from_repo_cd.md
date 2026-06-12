---
title: "fetch and store packages from repo cd"
date: 2006-12-30
forum: General Help
---

### Post by h.mehdi on 2006-12-30
Hi 

How should I set apt config files to fetch and store packages from an ubuntu repository CD ? I need packages to be copied and stored in /var/cache/apt/archives

Thanks

---

### Post by kvonb on 2006-12-30
Hello :)

Are you running Edgy (Ubuntu 6.10)?

If so then put your repository CD in the drive then open Synaptic, and look in the menu under "Edit" it has an option "Add CDROM".

That should do it.

Another way that I found is to copy the packages that you want installed, into /var/cache/apt/archives/partial/, then install the package as if you were doing it online, it picks them up from the partial folder rather than downloading them :).

It should work as long as there is not a newer version online.

Hope that helps.

Regards, Kev :)

---

### Post by h.mehdi on 2006-12-30
Thanks kvonb :) 

But this way apt will read from CD and install packages on my ubuntu box... I need these packages being copied and stored on my /var/cache/apt/archives.

---

### Post by kvonb on 2006-12-30
> **h.mehdi said:**
> Thanks kvonb :) 

But this way apt will read from CD and install packages on my ubuntu box... I need these packages being copied and stored on my /var/cache/apt/archives.

Do you mean that you want to create your own repository, say for your own network?  So that other computers on your network can install them from your computer?

If so, then I can't help you, maybe post in the "Network" section, you might have more luck.

Regards, KEv :)

---

