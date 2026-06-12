---
title: "reinstall"
date: 2008-06-10
forum: General Help
---

### Post by robinc on 2008-06-10
hi all.

basically my computer is a bit of a mess and I want to start from scratch but just keep my /var/www/ directory.

Is there any way of re installing and keeping this?

thank you :)

---

### Post by freduardo on 2008-06-10
A fresh install will reformat the partition.

So I would just back it up on external media (an usb stick or something similar) and then restore it afterwards.

---

### Post by ilrudie on 2008-06-10
> **freduardo said:**
> A fresh install will reformat the partition.

So I would just back it up on external media (an usb stick or something similar) and then restore it afterwards.

Agreed.  I would like to add then when you are rebuilding your box you will have the option to move portions of your file system to other partitions.  Its very common to have a separate /, /home, and /var for instance.  I personally don't have much need to /var and don't use it but it seems like you might want to think about it.  I'm not sure about what the install process writes to /var so you should make sure the install wont overwrite what you want to save but at least formatting / wont scrub your /var.

Also you could have the installer install /var in the root partition.  This of course can be fixed manually later to point /var to its nice separate partition once you are sure there is nothing in the new var that needs to be copied over.  Sorry if this is kinda hard to understand.  If you want me to take some more time to explain it better I would be glad to help.

---

### Post by robinc on 2008-06-10
ah man, this sucks I don't really have anything to back up onto :(.


I have Ubuntu server...if I remove ubuntu-desktop and reinstall would that maybe fix things.

The only problem is that I've put the hard drive in from my old computer into one I;ve built today and obviously all the graphics card drivers etc are from my old machine so it's a bit laggy and stuff.

---

