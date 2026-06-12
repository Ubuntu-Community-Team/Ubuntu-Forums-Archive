---
title: "RAID array not showing in Computer"
date: 2013-04-05
forum: General Help
---

### Post by marcerickson on 2013-04-05
I created a new array with new drives as a RAID 1 (mirror) on a CERC SATA 6-Channel RAID Controller in a Dell PowerEdge 1800 server.  Previously I used the card's Quick Init utility to initialize these two new 1 TB drives into a RAID 1 array.  After I did that, they showed in Computer as a 1 TB drive (as they should have) but I got an Access Denied error when I tried to create a text file on the array.

So I deleted the array and recreated it using the Clear function in the controller card BIOS.  The card reports during boot that the drives are Optimal - but I cannot see them in Computer.  Do I need to do something else?  Did I choose the wrong method to make the array?  Is it something else?

Thanks to all who read this and think about solutions for me.

---

### Post by marcerickson on 2013-04-05
Never mind.  I forgot I should create partitions and format them.  I feel very foolish.

---

