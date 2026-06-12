---
title: "[SOLVED] TomTom ONE Mounting Question"
date: 2007-06-10
forum: General Help
---

### Post by CaptainSteel on 2007-06-10
Hi I am trying to get Kubuntu to recognize my TomTom One and I am not having any luck. Kubuntu automatically detects any flash drive I connect, but it isn't doing the same for the TomTom. I'm assuming the TomTom memory is similar to an SD card. Any suggestions? Thanks

---

### Post by taurus on 2007-06-10
See if the kernel even detects it.  Open a terminal and post the output of this command here.

```
sudo fdisk -l
-or-
dmesg | tail
```

---

### Post by polt on 2007-06-10
It could be that it is just not auto-mounting.  Have you looked around in /dev to see if you could find it in there?

---

### Post by CaptainSteel on 2007-06-10
Thanks the code sudo fdisk -l helped me locate it. I guess it wasn't auto mounting. I created a desktop mount for it and now it works! Thanks Guys.

---

### Post by L34NN3 on 2007-08-22
Just a query - how did you do that?

---

