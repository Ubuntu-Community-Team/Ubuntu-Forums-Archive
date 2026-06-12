---
title: "installing wine"
date: 2005-06-09
forum: General Help
---

### Post by baseballer2150 on 2005-06-09
Well I'm new to linux, and have a question, just can't figure it out.  

Can someone walk me through how to install wine.  I can't figure it out after trying for the last hour so all help is appreciated.

Thanks

---

### Post by az on 2005-06-09
install wine, libwine wine-utils.  Install winetools from backports.  Run winesetup and follow the instructions for base setup.

---

### Post by gil-galad on 2005-06-09
He needs to install winesetuptk if he wants to run winesetup.

---

### Post by psychicdragon on 2005-06-09
1. First follow the steps located at this url to add all the repositories you'll need:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

2. Then type this in a terminal:
sudo apt-get install wine winetools

3. Then type this:
winetools
Select Base Install

To run a windows app you have to be in the directory where the exe resides then run:
wine yourapp.exe

---

### Post by az on 2005-06-09
Ack!  That was a typo.  winetools, not winesetup.

Winesetuptk is depreciated and does not work.

---

