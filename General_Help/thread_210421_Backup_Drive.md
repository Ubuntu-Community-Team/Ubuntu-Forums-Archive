---
title: "Backup Drive"
date: 2006-07-06
forum: General Help
---

### Post by thunderduck3141 on 2006-07-06
hi all
i have a second (configed as slave) ide 120 gig drive that is unformatted and i want to use it as a place to store backup info, i tried using the gui but each time i click "enable" nothing happens any ideas?

---

### Post by scxtt on 2006-07-06
which "gui" - gparted?

---

### Post by Denis on 2006-07-07
You will have to format the disk before you can enable it with the "Disks" utility. 

Start Gparted "Gnome Partition Editor" (or install this program with synaptic). 

Chose the harddisk you want to format. Make a new partition. You will now see that the rectagle (presenting your harddrive) has a color. Click apply to make the changes. 

Now your harddrive has a filesystem on it, and can be mounted (enabled).

---

