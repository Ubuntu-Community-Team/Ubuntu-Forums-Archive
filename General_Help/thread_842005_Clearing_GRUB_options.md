---
title: "Clearing GRUB options"
date: 2008-06-26
forum: General Help
---

### Post by Ramrod_The_Wizard on 2008-06-26
I've been running ubuntu for about a year now and have had little real problems after the initial bumps. I partitioned my drive so I could still occasionally use windows applications without the hassle of running them through WINE.  Since then, the amount of choices for ubuntu when using GRUB has increased and I'm wondering, how do I delete these redundant entries so it only gives me the choices I really need?

---

### Post by tamoneya on 2008-06-26
go into terminal and run these two commands: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo nano /boot/grub/menu.lst
```

Then scroll down to the bottom and delete(better yet comment out) the lines that correspond to older kernels and such.  If something gets really messed up just use the backup to get things working again.

---

### Post by bodhi.zazen on 2008-06-27
You have multiple entries because you have multiple kernels.

Remove the old kernels (it is always a good idea to keep at least 1 old one) and the removal process should clean up your grub menu.

---

### Post by Ramrod_The_Wizard on 2008-06-27
That's what I expected, but how do you get rid of the old kernels.

---

### Post by prince_niceguy on 2008-06-27
find the kernel in synaptic. they would be named as linux-image-<kernel version>. remove that and it will remove the line items.

---

### Post by WRDN on 2008-06-27
> **Ramrod_The_Wizard said:**
> That's what I expected, but how do you get rid of the old kernels.

To remove the old kernels, search for them in Synaptic Package Manager and remove them.
With regards to the removal of the entries in the menu.lst file, I would personally just comment out the lines, rather than removing the entries. That way, if you still have the kernel and have to access it for whatever reason, you could easily uncomment the line(s).
To do this, just put a # before the title line for each entry you wish to remove.

---

