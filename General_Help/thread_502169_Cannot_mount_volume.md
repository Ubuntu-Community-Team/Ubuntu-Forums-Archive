---
title: "Cannot mount volume"
date: 2007-07-16
forum: General Help
---

### Post by Infinity-al on 2007-07-16
Hi,

I have a problem when inserting a dvd on my dvd-rom. It gives this error message:

Cannot mount volume

Invalid mount option when attempting to mount the volume '©Data Center06'.

It gives this error only with that dvd all the others cd and dvd i insert work great.

Please help,]

thanks in advance

---

### Post by Happy_Man on 2007-07-16
I think it's because of the Copyright symbol. I'm pretty sure that that copyright symbol isn't recognized and prevents just that DVD from mounting.

---

### Post by Infinity-al on 2007-07-16
Is there anyway to fix it ?

---

### Post by Happy_Man on 2007-07-16
> **Infinity-al said:**
> Is there anyway to fix it ?
Sorry, no. That's the DVD's fault, not Ubuntu's.

---

### Post by Infinity-al on 2007-07-17
> **Happy_Man said:**
> Sorry, no. That's the DVD's fault, not Ubuntu's.
Ok... Thanks anyway

---

### Post by littleguy on 2007-07-24
> **Infinity-al said:**
> Hi,

I have a problem when inserting a dvd on my dvd-rom. It gives this error message:

Cannot mount volume

Invalid mount option when attempting to mount the volume '©Data Center06'.

It gives this error only with that dvd all the others cd and dvd i insert work great.

Please help,]

thanks in advance


hi, i have the same problem with my data DVD

read this [http://ubuntuforums.org/showthread.php?t=500820](http://ubuntuforums.org/showthread.php?t=500820)

please back up your **/etc/fstab** file

then try edit /etc/fstab

**sudo gedit /etc/fstab**

replace [COLOR="DarkRed"]**udf,iso9660 user**[/COLOR]  with   [COLOR="DarkRed"]**auto	users**[/COLOR]

this fix my problem

---

