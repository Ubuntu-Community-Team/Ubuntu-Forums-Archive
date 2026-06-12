---
title: "update error message"
date: 2013-07-11
forum: General Help
---

### Post by Kato4059 on 2013-07-11
I have been using LXLE 12.04 -32. recently when there are upgrades ,and I try to install then an error dialog appears with the following msg. "please insert Lununtu 13.04 I386 ,but when In try Lununtu 13.04 or the LXLE live dvd ,they are not found. 
Thanking you ,
kat4059

---

### Post by Cheesehead on 2013-07-11
That's right, the updates are not on your DVD. You probably knew that already.

Edit your /etc/apt/sources.list and comment out the DVD.
If you have trouble finding it, post the file here.

---

### Post by Kato4059 on 2013-07-12
> **Cheesehead said:**
> That's right, the updates are not on your DVD. You probably knew that already.

Edit your /etc/apt/sources.list and comment out the DVD.
If you have trouble finding it, post the file here.

/etc/apt/sources.list.d/anonbeat-guayadeque-precise.list
/etc/apt/sources.list.d/anonbeat-guayadeque-precise.list.save
/etc/apt/sources.list.d/cooperjona-stormcloud-precise.list.save
/etc/apt/sources.list.d/deluge-team-ppa-precise.list
/etc/apt/sources.list.d/deluge-team-ppa-precise.list.save
/etc/apt/sources.list.d/ehoover-compholio-precise.list
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save
/etc/apt/sources.list.d/getdeb.list
/etc/apt/sources.list.d/getdeb.list.save
/etc/apt/sources.list.d/kevin-mehall-pithos-daily-precise.list
/etc/apt/sources.list.d/kevin-mehall-pithos-daily-precise.list.save
/etc/apt/sources.list.d/libreoffice-ppa-precise.list
/etc/apt/sources.list.d/libreoffice-ppa-precise.list.save
/etc/apt/sources.list.d/lubuntu-desktop-ppa-precise.list
/etc/apt/sources.list.d/lubuntu-desktop-ppa-precise.list.save
/etc/apt/sources.list.d/lubuntu-dev-non-official-apps-precise.list
/etc/apt/sources.list.d/lubuntu-dev-non-official-apps-precise.list.save
/etc/apt/sources.list.d/lubuntu-dev-staging-precise.list
/etc/apt/sources.list.d/lubuntu-dev-staging-precise.list.save
/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/medibuntu.list.save
/etc/apt/sources.list.d/noobslab-deepin-sc-precise.list
/etc/apt/sources.list.d/noobslab-deepin-sc-precise.list.save
/etc/apt/sources.list.d/openshot_developers-ppa-precise.list
/etc/apt/sources.list.d/openshot_developers-ppa-precise.list.save
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.save
/etc/apt/sources.list.d/playdeb.list
/etc/apt/sources.list.d/playdeb.list.save
/etc/apt/sources.list.d/richardgv-compton-precise.list
/etc/apt/sources.list.d/richardgv-compton-precise.list.save
/etc/apt/sources.list.d/shimmerproject-ppa-precise.list.save
/etc/apt/sources.list.d/shnatsel-zram-precise.list
/etc/apt/sources.list.d/shnatsel-zram-precise.list.save
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save
/etc/apt/sources.list.d/upubuntu-com-chat-precise.list
/etc/apt/sources.list.d/upubuntu-com-chat-precise.list.save
/etc/apt/sources.list.d/videolan-master-daily-precise.list
/etc/apt/sources.list.d/videolan-master-daily-precise.list.save

---

### Post by Kato4059 on 2013-07-12
Hope this helps; I opened a few ,and there was no mention of DVD.
thanking you,
kato4059

---

### Post by Kato4059 on 2013-07-12
Thanks ,Cheesehead.
As you suggested ,I accessed the files ,and after sending the files to you ,I went back and found the cd ref. unticked the box ,and updated the packages. 
So SOLVED
kato4059

---

