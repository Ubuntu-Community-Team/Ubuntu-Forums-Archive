---
title: "How do I get Grub to boot Ubuntu &amp; XP?"
date: 2006-08-22
forum: General Help
---

### Post by epicurus on 2006-08-22
Hi,

Not sure if this is in the right place or not.  Sorry if its not.

I have 2 HDD's and I have Ubuntu installed on one and XP on the other.

My question is this.  I want to add the 2 HDD to Grub to allow me to either boot into windows or Ubuntu.

If you can help or point me to a good guide that would be briliant.  New to Linux and learning fast :D 

Many thanks in advance

John

---

### Post by PriceChild on 2006-08-22
If windows is on a separate harddrive, then you need  a more complex solution to your grub menu.lst to if its on different partitions.
 
Unfortunately my pc is currently recovering after dying completely a couple of days ago. It's been fscking for the past hour or two but will post the important bit of my grub as soon as i can.

---

### Post by epicurus on 2006-08-22
Sorry to hear about your PC problems

That would be great if you could post some info

Thanks

---

### Post by epicurus on 2006-08-25
anyone help here with this?

---

### Post by tormod on 2006-08-25
Check the official grub documentation
[http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows)
for how to use the "map" command.

---

### Post by h00s on 2006-08-25
Add this to /boot/grub/menu.lst
```
title           Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
chainloader     (hd1,0)+1   
makeactive
```hd0 - ubuntu
hd1 - winxp

---

