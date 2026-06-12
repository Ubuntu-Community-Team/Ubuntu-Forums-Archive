---
title: "Boot right into Ubuntu?"
date: 2007-08-30
forum: General Help
---

### Post by shrumhead on 2007-08-30
I was recently dual-booting Ubuntu/Windows but I decided to do away with windows completely and just use the extra space for Ubuntu.  Now that I am only booting 1 OS, how do I have my comp boot straight into Ubuntu instead of going through grub?

---

### Post by forestpixie on 2007-08-30
it's going to use grub - as win uses mbr

you can change the menu.lst to a different time out, open aterminal

```
sudo cp /boot/grub/menu.lst  /boot/grub/menu.bak.3008
```

for a backup

```
gksudo gedit /boot/grub/menu.lst
```

and find this section 


```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2
```

and change the time to suit - I use 2 secs gives me enough time if ther's a problem and I need to use recovery or the other kernel

---

### Post by kellemes on 2007-08-30
Nice solution..
[http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu")

---

### Post by forestpixie on 2007-08-30
> **kellemes said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu")

Yea - I did that to start with and kept forgetting to press esc - so I changed to this solution :D - better for me

---

### Post by shrumhead on 2007-08-30
Thanks much, worked like a charm.

---

