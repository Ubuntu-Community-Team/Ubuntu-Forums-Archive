---
title: "Unable to shut Ubuntu down properly after installing fglrx"
date: 2013-02-06
forum: General Help
---

### Post by bargaho on 2013-02-06
Hi guys,

I am currently running 64-bit Ubuntu 12.10 installed via Wubi with Gnome Shell 3.6. I installed the Catalyst Legacy driver using this [method]("http://www.ubuntugeek.com/how-to-install-amd-catalyst-legacy-drivers-in-ubuntu-12-10-quantal.html") for my HD4850.

However, I noticed that Ubuntu now hangs whenever I shut it down or try to restart after using it for a bit. I tried check the forums, and mostly got variations of this [method]("http://mylinuxexplore.blogspot.com/2011/11/solved-ubuntu-doesnt-shutdown-properly.html"). I think it's related to fglrx. Is there any way I can fix the shutdown issue?

Thanks in advance

---

### Post by c2tarun on 2013-02-06
> **bargaho said:**
> Hi guys,

I am currently running 64-bit Ubuntu 12.10 installed via Wubi with Gnome Shell 3.6. I installed the Catalyst Legacy driver using this [method]("http://www.ubuntugeek.com/how-to-install-amd-catalyst-legacy-drivers-in-ubuntu-12-10-quantal.html") for my HD4850.

However, I noticed that Ubuntu now hangs whenever I shut it down or try to restart after using it for a bit. I tried check the forums, and mostly got variations of this [method]("http://mylinuxexplore.blogspot.com/2011/11/solved-ubuntu-doesnt-shutdown-properly.html"). I think it's related to fglrx. Is there any way I can fix the shutdown issue?

Thanks in advance

Can you please try executing 
```
sudo shutdown -h now
```
and please tell whether its still hanging or its shutting down properly?

---

### Post by bargaho on 2013-02-06
Thanks for the quick reply! I've tried using sudo shutdown with -r, -h, and -P. None of them work.

---

