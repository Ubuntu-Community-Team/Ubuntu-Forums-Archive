---
title: "Internal drives do NOT appear in Nautilus in 17.10"
date: 2017-12-31
forum: General Help
---

### Post by David4321 on 2017-12-31
I used to be able to see ALL my mounted and unmounted internal drives in the left hand pane in Nautilus. Now after installing 17.10 they do not appear. (external drives appear as normal) Internal drives can only be seen under "Other Locations", and drive properties are not an option in the context menu (right click). This was my common way to view the total contents (used space) and free space on the drives, with the familiar pie chart. None of these drives can be added to the left hand pane as a bookmark either. Further, when clicking into "Computer" (OS drive), select all, and view combined properties, something inside it tallies immense TB's of contents before I quit the properties dialog without a result. I've noticed this effect before with this operation, but it did not affect the pie chart tally of drive space in properties. 

How can I get all internal drives back on the left hand pane in Nautilus, including the properties dialog? 

Thanks.

---

### Post by Dennis N on 2017-12-31
You would want to use **Disk Usage Analyzer** instead. It will show total usage for file system on each internal and external partition that's mounted. See screen shot attached. An external USB drive I have connected is shown last in the list.

Also, clicking on any of these will give a new window with details and ring chart of each file system usage.

---

### Post by mc4man on 2017-12-31
You can't, this is the direction nautilus dev's have decided to go.
If inclined you could use a different file manager. Screens show what I have here in 18.04(dev) using nemo. Also notice that mounted partitions also have a little bar graph under the partition that shows how full. (media & the 100GB are almost full, the 162Gb is only around 1/4 used.

---

### Post by David4321 on 2018-01-02
> **mc4man said:**
> You can't, this is the direction nautilus dev's have decided to go.
If inclined you could use a different file manager. Screens show what I have here in 18.04(dev) using nemo. Also notice that mounted partitions also have a little bar graph under the partition that shows how full. (media & the 100GB are almost full, the 162Gb is only around 1/4 used.

Awesome! That's great, I'll just stick with Nemo. It's better in a number of important ways. Thanks.

---

