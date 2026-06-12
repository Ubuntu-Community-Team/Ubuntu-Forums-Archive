---
title: "920316 - obtaining a driver for ubuntu from fedora"
date: 2013-06-09
forum: General Help
---

### Post by hamidi on 2013-06-09
a linux driver is given for a DVR card just for Fedora 8. i want its  driver for Ubuntu 12.04. source of driver is not present. can i write a  wrapper to use the present api's in the driver of fedora 8 in ubuntu?  it's in assembly language anyway and use ports etc.
we really need a driver for ubuntu for the card.

---

### Post by Cheesemill on 2013-06-09
What is the make/model of the card?

---

### Post by hamidi on 2013-06-09
Hikvision DS-4216 HCI DVR Card

---

### Post by hamidi on 2013-06-09
there're two kinds of cameras, network cameras and local (analog) cameras. until now, we used to put the DVR card in a system's slot with Windows OS. the driver for Windows is available, but for ubuntu. now, we want to put the card in the server not to have to connect to the analog cameras via a remote system. so we need ubuntu to know it and may work with the card. by this way, we may use the same system for servicing and not have to have two systems.

---

### Post by 3rdalbum on 2013-06-09
A binary driver from 2007 wont run on a kernel from 2012, or indeed a kernel from 2008 or 2006. If there is no open source driver available or preinstalled in Ubuntu, then there is no way to make the camera work. Sorry.

---

