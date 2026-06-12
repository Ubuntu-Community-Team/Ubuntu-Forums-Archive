---
title: "does my card support compiz?"
date: 2008-06-27
forum: General Help
---

### Post by mahmater on 2008-06-27
I am following instructions to install compiz on my ubuntu desktop but when I go to system_____administration_________hardware drivers to enable graphic cards I just find nothing listed.
in terminal I run: lspci -nn | grep VGA

and here is the output:
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)

my question: can i run compiz with such a card?

thank you in advance.

---

### Post by Kevbert on 2008-06-27
Try running compiz-check, you can find it [here]("http://forlong.blogage.de/article/pages/Compiz-Check").
Yes you can run compiz.  A [problem]("http://forum.compiz-fusion.org/showthread.php?t=1093&highlight=82845G") was posted on the compiz web site which suggests you can!!!

---

### Post by mahmater on 2008-06-28
many thanks kevbert.

now the problem as I told u is that no card ever shows on harware drivers window!!!!!!!!!!!

---

### Post by Forlong on 2008-06-28
> **mahmater said:**
> now the problem as I told u is that no card ever shows on harware drivers window!!!!!!!!!!!
That's not a problem. Your hardware doesn't need additional drivers.

The intel drivers are open source, thus they are freely distributable.
This way, Ubuntu can ship them by default. :)

---

### Post by mahmater on 2008-06-28
thanx 4 help. I now installed compiz and I have just learnt to run the cube!!!

---

### Post by Forlong on 2008-06-29
This should be of help: [http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

Have fun. :)

---

