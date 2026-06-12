---
title: "Ubuntu 15.04 brightness keys do not work on Toshiba Tecra"
date: 2015-04-26
forum: General Help
---

### Post by echosmart on 2015-04-26
Hi !

I-m install new version of Ubuntu 15.04 in my laptop toshiba tecra.
In this version the brightness key working but not setting the screen luminosity.

I-ts possible to solve this ?
Thanks for all ansvers !

Sorry for my english !

---

### Post by echosmart on 2015-04-26
Solved !

sudo cp /etc/default/grub /etc/default/grub.ORIG
sudo apt-get install gedit gksu
gksu gedit /etc/default/grub

exchange this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
with this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet **acpi_backlight=vendor**"

save with same name

sudo update-grub

sudo reboot

[Thanks for ]("http://ubuntu.hu/node/39903")[ubuntu.hu forum]("http://ubuntu.hu/node/39903") !
sudo reboot

---

### Post by pankajkundlia on 2015-07-11
I tried this and some more similar grub file editing but no results in my Lenovo V470 running Ubuntu 15.04

---

### Post by pankajkundlia on 2015-07-13
anyone else facing issue with brightness control in ubuntu 15.04???

---

### Post by yan-foto on 2015-09-02
I had the same issue with Lenovo U410 and the provided solution worked fine. It is however a little bit buggy :(

---

