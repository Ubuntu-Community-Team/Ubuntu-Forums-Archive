---
title: "Kernel 2.4"
date: 2004-10-14
forum: General Help
---

### Post by pgarcia on 2004-10-14
Hi,

Is it possible to install kernel 2.4 with Ubuntu through apt?

Thanks

---

### Post by daniels on 2004-10-14
[quote=pgarcia]Is it possible to install kernel 2.4 with Ubuntu through apt?[/quote]

Yes, if you enable the 'universe' repository (see our FAQs for instructions on how to do that).  However, 2.4.x is unsupported under Ubuntu, and you'll need to edit your XF86Config-4 to disable /dev/input/mice (probably change it to /dev/psaux), and a few other things just won't work out of the box.

---

### Post by pgarcia on 2004-10-14
Thanks. I did what you said and I could install it. Unfortunatelly some drivers stops to work (of course)...

My ideia is to use Ubuntu as my developmente plataform and I have some drivers under 2.4 kernel.

May be I´ll use it to upgrade theses drivers to 2.6 kernel.

Thanks

Paulo Garcia

---

### Post by articpenguin on 2008-05-24
is it possible to get 2.4 kernels in hardy?

---

