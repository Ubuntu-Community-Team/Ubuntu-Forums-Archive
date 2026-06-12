---
title: "Best Wireless Card for Ubuntu?"
date: 2007-02-06
forum: General Help
---

### Post by CocoAUS on 2007-02-06
I'm looking for a G wireless card for my PC that works out of the box.  I also use the nVida drivers, and I understand that removing the restricted modules (done during driver installation) can mess with some wireless cards, so I'll need one that works with the nVidia drivers without a problem.

Any time tested and approved cards you know of?

I'm presently using ndiswrapper to get my Belkin to work, but it won't connect to most networks.  I can see about 8 networks in my neighborhood, and the card only consistently connects to one of them, rarely to one or two of the others, and never to my own network.  So I'd like to get rid of this stupid cable running across the floor, and any suggestions you guys have would be much appreciated.

---

### Post by g8m on 2007-02-06
Dont know which one is best, my netwerk controller intel corporation pro/wireless 2200BG (rev 05) worked out of the box, but it is an oldie.

---

### Post by Rich78 on 2007-02-06
nVidia is a graphics driver, it should have no impact on wireless drivers.

This link should help:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by CocoAUS on 2007-02-06
Thanks for the link, but it seems to be seriously outdated, and does not address the issue of restricted modules.

Installing the nVidia drivers requires the removal of the linux restricted modules.  These files are required for some wireless cards, so many (including myself) have had problems with wireless devices after installing the nVida driver.

---

### Post by fragos on 2007-02-07
System-> Administration-> Synaptic Package Manager-> Search for and install "nvidia-glx".

---

### Post by Skidpad on 2007-02-07
Here's me: [http://www.newegg.com/Product/Product.asp?Item=N82E16833320105]("http://www.newegg.com/Product/Product.asp?Item=N82E16833320105")

Works great!  Read the user reviews; quite a few X users find happiness with this card.

---

