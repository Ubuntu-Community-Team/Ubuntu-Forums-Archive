---
title: "Problem in Synaptic"
date: 2007-02-22
forum: General Help
---

### Post by tawniteamo on 2007-02-22
I just installed Xubuntu Edgy Eft 6.10 and whenever I try to update in Synaptic, it will start downloading the packages, but then tells me to insert the edgy eft cd, an when I do, it contiues asking for it. I am new to linux and this is my first install with the alternate cd.

---

### Post by tzulberti on 2007-02-22
You should change the source.list, so it doesn't include the CD. For doing this, do the following:
-> Open Synaptic
-> Go to Setting, Repositories. 
-> Delete or uncomment the cd option (I dont know which option is becuase i am not in my Pc)

---

### Post by tawniteamo on 2007-02-23
> **tzulberti said:**
> You should change the source.list, so it doesn't include the CD. For doing this, do the following:
-> Open Synaptic
-> Go to Setting, Repositories. 
-> Delete or uncomment the cd option (I dont know which option is becuase i am not in my Pc)
I was going to do as you suggested, but I had already shutdown after doing using the update manager, not synaptic, and it reboots with the following message:

"Server Authorization Directory (daemon/ServAuthDir) is set to /var/lib/gdm but is not owned by user root and group gdm. Please correct ownership or GDM configuration and restart GDM."

have any more advice?

---

