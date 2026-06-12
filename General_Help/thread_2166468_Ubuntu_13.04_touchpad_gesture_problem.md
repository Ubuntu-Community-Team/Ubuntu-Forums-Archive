---
title: "Ubuntu 13.04 touchpad gesture problem"
date: 2013-08-09
forum: General Help
---

### Post by majalcmaj on 2013-08-09
Hi!
I have just installed Ubuntu 13.04 on my new notebook. Although it`s working perfectly, I can`t set it to read multitouch gestures. I tried various drivers, but none of them worked. I couldn`t finish the installation of synaptics driver successfully. I installed synaptiks from ubuntu software center, but it needed synaptics driver. Xinput recognises my touchpad as PS/2 Elantech Touchpad. My computer is Samsung 730u. I would really enjoy some help.
PS. Please, don`t ask me to search for the solution in google. I spent almost 3 hours there, but I found nothing there.
Thanks for replies!

---

### Post by SweetAurora on 2013-08-09
Have you tried Ubuntu's official Multitouch troubleshooting page?
[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

---

### Post by majalcmaj on 2013-08-09
It doesn`t bring any solution for me. I read there that Elan touchpads are supported, but I still don`t know how to deal with the problem.

---

### Post by majalcmaj on 2013-08-30
OK, looks like my problem is solved. I reinstalled the system twice. The usage of moltitouch gestures was disabled in synaptics, I have just changed values using ```
synclient "VertTwoFingerScroll"=1
``` Problem solved, thread may be closed. Thanks for help.

---

