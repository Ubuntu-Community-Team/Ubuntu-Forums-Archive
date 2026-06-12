---
title: "S.M.A.R.T and HD-Cloning"
date: 2007-04-24
forum: General Help
---

### Post by Helmi on 2007-04-24
Hi,

sorry for mixing two topics up but they're kinda related ;)

I booted the windows on my pc after a few days and HDDHealth (SMART-Status Tool for Windows) reported several Problems with the HD. It's nothing unexpected and i already have a spare drive here.

So two questions now:

1. How do i mirror the drive i have now? Are there free (as in free speech or in free beer, however) tools for that? probably tools on a LiveCD like Knoppix? Otherwise i could probably use acronis for that -  i still have a licence.

2. Is there a good solution to have S.M.A.R.T-Status monitored under ubuntu?

Thanks for your help!

---

### Post by Alekc on 2007-04-24
Hmm for the first point if you still have acronis, why not :P
For the second... if you want misure it's temp there is hddtemp, otherwise smartmontools maybe, not too sure anyway :(

---

### Post by Helmi on 2007-04-24
> Hmm for the first point if you still have acronis, why not :P

open source is soo much smarter ;)

> otherwise smartmontools maybe, not too sure anyway 

i'll give it a shot - thanks!

---

### Post by Helmi on 2007-04-25
i got it cloned with Acronis now. In case anyone get's to this thread searching for hd clone tools. I burned the new [Ultimate Boot CD]("http://www.ultimatebootcd.com") (free) a few minutes ago and it now has a completely new Clone HD section with free tools. Probably you should get it also due to some other great tools.

---

### Post by dcstar on 2007-04-25
> **Helmi said:**
> i got it cloned with Acronis now. In case anyone get's to this thread searching for hd clone tools. I burned the new [Ultimate Boot CD]("http://www.ultimatebootcd.com") (free) a few minutes ago and it now has a completely new Clone HD section with free tools. Probably you should get it also due to some other great tools.

If you have a working system, you can probably use the Partition Copy feature in Gparted as well.

Cloning's good if you have an identical (or bigger) second drive, but sometimes just copying your important partitions one by one can be handy.

---

### Post by Helmi on 2007-04-25
> but sometimes just copying your important partitions one by one can be handy

yeah that's right but in this case you have to manually reconfigure the mbr stuff (manual grub install and stuff).

In my case the hdd's were both the same size (even nearly the same type/manufacturer) so cloning was the best and quickest solution. took me exactly 10 minutes with acronis and the system was up again.

---

