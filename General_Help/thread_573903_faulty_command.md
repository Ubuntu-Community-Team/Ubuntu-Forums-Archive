---
title: "faulty command?"
date: 2007-10-12
forum: General Help
---

### Post by pennyminstrel on 2007-10-12
I´m trying to add a custom application launcher to the panel which will open a specific folder, something I´ve done before, but having no luck. 

The command I´m using is

 nautilus /media/sda2/´My Files´

Every time I click the launcher I get two messages, one saying 

]Couldn't find "/media/sda2/´My".    and the other 

Couldn't find "/home/penny/Files´ !!!

I can´t work out what I´m doing wrong. Can anyone help?


Penny

---

### Post by thirddeep on 2007-10-12
I am unsure why you have "''My files'" in there ?

Just 
```
nautilus /media/sda2/
```
will open that directory.

Thd.

---

### Post by banewman on 2007-10-12
I'm a long way away so this is a guess but if you look in the /media file you will see the mount point for sda2 - it might be called something else?

---

### Post by pennyminstrel on 2007-10-12
Hi guys

Thanks for your input both of you. 

The reason I had 'My Files' in there was cos that was the folder in sda2 I wanted the launcher to open. However it's amazing what coming back fresh to things does. I realised I only needed the quote around 'My Files' not the whole thing and bingo it worked!

Sorry to be so thick

Penny

---

