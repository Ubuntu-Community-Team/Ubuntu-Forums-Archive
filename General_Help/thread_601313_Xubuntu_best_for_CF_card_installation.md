---
title: "Xubuntu best for CF card installation?"
date: 2007-11-03
forum: General Help
---

### Post by njparton on 2007-11-03
I've got a headless NAS up and running using an old SATA drive as a boot disk. My ultimate aim is to migrate this to an 8GB CF card via an IDE adapter to save space, heat and noise.

I tried this last night using Feisty 7.04 32 bit and the performance was appalling. It took about 1.5 hours to install alone, and was then very very sluggish.

Does anyone have any experience of running Xubuntu (with Xcfe) from a CF card? Is it worth a shot?

---

### Post by njparton on 2007-11-06
Well, if anyone's insterested, the answer is no.

CF cards seem best suited to steamlined distros such as FreeNAS and Openfiler.

Performance with Ubuntu and Xubuntu is very poor (basically not useable day to day).

I'm going to stick with a small hard drive instead.

---

### Post by Mithrilhall on 2007-11-06
What type of CF card reader and what type of CF are you using?

---

### Post by njparton on 2007-11-06
I got a CF to IDE adapter off eBay for a few £ and a Sandisk 8GB CFIII card.

I'll probably just end up using it in my digital camera now :(

Do you know of any performance tweaks?

It took 60 mins to install Xubnutu last night once I'd answered all the initial questions.

---

### Post by Mithrilhall on 2007-11-06
What speed is the card, 133, 266?

---

### Post by njparton on 2007-11-06
133 I think.

Do you have a similar issue?

---

### Post by Mithrilhall on 2007-11-07
I built a system running Debian and I was using a 133 speed CF. I believe there are 266 out there so I would go with something like that.

I ended up with a 4GB CF that I couldn't use with my CF reader (it wasn't bootable) and my camera is a fat32 system (2GB limit).

---

### Post by njparton on 2007-11-07
How did the debian system perform?

---

### Post by Mithrilhall on 2007-11-07
The install was slow but I was using the x133 speed CF. I'm sure the x266 speed would be much better.

Once the OS was installed it performed pretty well.

I found this after I already installed Debian, it is a version of Debian built for CF.

[http://shopping.hacom.net/catalog/product_info.php?products_id=52](http://shopping.hacom.net/catalog/product_info.php?products_id=52)

---

### Post by njparton on 2007-11-07
I bought my CF card when I was considering Openfiler or FreeNAS but in the end I decided against them due to limited sleep functions. Not ideal for a home nas.

---

