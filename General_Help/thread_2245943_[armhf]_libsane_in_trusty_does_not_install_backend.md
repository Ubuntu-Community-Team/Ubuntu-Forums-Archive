---
title: "[armhf] libsane in trusty does not install backend configs in /etc/sane.d/"
date: 2014-09-27
forum: General Help
---

### Post by lukasfischer on 2014-09-27
Hi, i am using lubuntu on a odroid.
During scanner installation i noticed, that no backend configs are present in the /etc/sane.d/ folder. I tried apt-get install --reinstall libsane without success, it stays empty except of one subfolder:
```
lukas@odroid:/etc/sane.d$ find . -name \* -print
.
./dll.d

```
On an old 12.04 machine it show up as:
```
lukas@odroid:/etc/sane.d-bak$ find . -name \* -print
.
./artec.conf
./canon_pp.conf
./bh.conf
./dll.conf
./v4l.conf
./magicolor.conf
./qcam.conf
./hpsj5s.conf
./pie.conf
./genesys.conf
./dell1600n_net.conf
./avision.conf
./gphoto2.conf
./mustek_pp.conf
./st400.conf
./dc210.conf
./umax_pp.conf
./coolscan.conf
./geniusvp2.conf
./hp.conf
./u12.conf
./sceptre.conf
./gt68xx.conf
./canon.conf
./dc25.conf
./net.conf
./rts8891.conf
./mustek_usb.conf
./apple.conf
./hp4200.conf
./coolscan2.conf
./fujitsu.conf
./canon_dr.conf
./epson.conf
./hp5400.conf
./coolscan3.conf
./umax1220u.conf
./dmc.conf
./lexmark.conf
./abaton.conf
./s9036.conf
./ibm.conf
./hs2p.conf
./dll.d
./dll.d/hplip
./dll.d/libsane-extras
./plustek_pp.conf
./cardscan.conf
./mustek.conf
./sharp.conf
./leo.conf
./ma1509.conf
./microtek2.conf
./epson2.conf
./xerox_mfp.conf
./teco2.conf
./hp3900.conf
./agfafocus.conf
./nec.conf
./teco1.conf
./kodak.conf
./umax.conf
./saned.conf
./plustek.conf
./ricoh.conf
./snapscan.conf
./p5.conf
./microtek.conf
./pixma.conf
./matsushita.conf
./sm3840.conf
./sp15c.conf
./stv680.conf
./artec_eplus48u.conf
./test.conf
./epjitsu.conf
./teco3.conf
./tamarack.conf
./canon630u.conf
./dc240.conf

```

sane works, if i add the /etc files manually which are present in the .deb package.
Version is libsane_1.0.23-3ubuntu3.1_armhf.
Did anyone encounter this on other platforms too? Is this a bug or some strange problem in my apt setup?
Thanks, Lukas

---

