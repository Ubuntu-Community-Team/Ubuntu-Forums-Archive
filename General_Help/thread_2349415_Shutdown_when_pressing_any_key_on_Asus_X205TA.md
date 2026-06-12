---
title: "Shutdown when pressing any key on Asus X205TA"
date: 2017-01-14
forum: General Help
---

### Post by choiz on 2017-01-14
Hi,

I have setup a fresh install of xubuntu 16.10 and on my login-manager when I press key it's shutdown the computer.
I log me with the virtual keyboard, and under xfce when I press keyboard it display the "logout / shutdown / reboot menu".

I setup openssh-server and try to cat the /var/log/syslog when I press a key on the login screen but nothing strange was log.

I replace the lightdm login manager by slim, same problem (so the problem was before the login manager but where?)

Is anyone know why?

Regards,

---

### Post by choiz on 2017-01-14
I fix the problem! 

The kernel 4.8.0-34-generic doesn't works so the 4.8.0-22-generic works fine.

---

### Post by harryharryharry on 2017-01-24
anyone coming here from google:
the keyboard malfunction can be solved by reverse patching the kernel sources with this patch:
[https://www.spinics.net/lists/linux-gpio/msg18340.html](https://www.spinics.net/lists/linux-gpio/msg18340.html)

hopefully this will be solved soon in the offical stock kernels/kernel sources...

---

