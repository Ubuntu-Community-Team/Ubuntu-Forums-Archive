---
title: "Problems after testing battery support"
date: 2005-10-19
forum: General Help
---

### Post by Klenje on 2005-10-19
Hi, I have a Acer Aspire 1692 and I have installed successfully Breezy on it. But then I tried to enable battery support through dsdt... the result was a freeze immediately after grub menu; but the worst thing is that even old kernel image doesn't work... after starting x it appears the text Battery status check and the system freezes... is there a way to restore previous image? or I just have to reinstall everything? Thanks

---

### Post by blacknet on 2005-10-20
i´m configuring the kubuntu system with acer 1692 wlmi.

when i finish i´ll post the instructions for configuring your machine.

;)

---

### Post by Klenje on 2005-10-24
any news? I installed breezy from scratch and now ethernet connection  doesn't work... with hoary it was detected without any problem... anyone knows how to make it work?

---

### Post by blacknet on 2005-10-24
the wireless and ehternet work 100%. the batery marker must be configured with DSDT but in 5.10 version dont work.

when funtionality of acer been 100% i post here the result.

---

### Post by Klenje on 2005-10-24
thanks, I will appreciate your result a lot... did you install breezy from scratch or  just as upgrade? because I found that my ethernet doesn't work just if I install from scratch, if I upgrade it works... that's very strange....

---

### Post by blacknet on 2005-10-26
well im studing the problem and the results is that kubunt 5.10 (breezy) don´t works with acer in this moment.

But kubuntu and ubuntu 5.04 (hoary) works fully perfectly.

the intruccions for instalation are here.

[http://translate.google.com/translate?u=http://weblog.topopardo.com/archives/000270.html&langpair=es%7Cen&hl=en&ie=UTF8](http://translate.google.com/translate?u=http://weblog.topopardo.com/archives/000270.html&langpair=es%7Cen&hl=en&ie=UTF8)

in the four point you must put.

$sudo dpkg-reconfigure linux-image-2.6.9-5-686 (you must install the 686 kernel).

Bye my frien good luck.

when the colony or hoary versions of 5.10 are released i will work with them.

sorry for my little english.

---

