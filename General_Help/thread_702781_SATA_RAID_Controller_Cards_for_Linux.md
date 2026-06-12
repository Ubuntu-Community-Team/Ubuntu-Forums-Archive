---
title: "SATA RAID Controller Cards for Linux"
date: 2008-02-20
forum: General Help
---

### Post by chris.zeman on 2008-02-20
I am going to install Ubuntu Server 7.10, and want to use some SATA drives for some SAMBA shares. Has anyone tried the PNY P-DSA150-PCI-RF SATA RAID PCI Card? I'm looking at one on Tiger Direct at [http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3505320&body=QA#tabs]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3505320&body=QA#tabs"). I'm open to other recommendations as well, but I'm on a tight budget. :(

Thank you,
Chris

---

### Post by ahsile on 2008-02-20
How many drives/what type of raid are you going to build? I just created a software RAID 1 with the information available on the forums here, and a friend of mine was successful with a software RAID 5 using the same info. 

I guess what I'm getting at is do you really need an expensive raid controller?

---

### Post by fjgaude on 2008-02-20
There is no mention of a driver for Linux, and without such you will have to use dmraid software to recognize the array. This will not be easy.

The PCI-e card is a good deal for those who don't have a motherboard with PCI-e controller onboard.

---

### Post by chris.zeman on 2008-02-21
My plan is, at some point, to have 6 or 8 drives (3 or 4 mirrored sets). I originally wanted to use NAS enclosures, but figured I would weigh all my options. I'm thinking that I really wouldn't gain anything going the route of a bunch of SATA drives connected to a PC. It would probably be better for me to just invest in some Buffalo LinkStations, which is what I originally wanted to do. :)

Thank you,
Chris

---

