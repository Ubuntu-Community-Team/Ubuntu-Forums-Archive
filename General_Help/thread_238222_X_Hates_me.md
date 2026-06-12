---
title: "X Hates me"
date: 2006-08-17
forum: General Help
---

### Post by rekahsoft on 2006-08-17
ok...i got a box that i am setting up as a server...i was going to put ubuntu on as my OS but when i booted (using onboard grapphics) X complained about no detecting my monitor and hardware...so i grabed a spair video card i had around (which has been tried and tested and works fine) and then tried again with the same results...so i switched the monitor and the same results...i was then going to install gentoo 2006.0 but it is the biggest pain in the butt to install so i decided i would try my solaris 10 cd's...what do you know...Solaris detected my video card and started x fine. I still want o run ubuntu on it because i know it well...how do i fix my little X/detection problem?

Note: If you need the exact output i can type it out for you :) Thanx

---

### Post by taurus on 2006-08-17
Assuming that you already have a basic Ubuntu running on your machine, then you can configure X with 

```

sudo dpkg-reconfigure xserver-xorg

```
But if you try to install but can't boot from the desktop CD, aka LiveCD, then try to use the alternate CD instead...

---

### Post by rekahsoft on 2006-08-17
hmmm..ok so i can't use the live cd installer.

---

### Post by taurus on 2006-08-17
The alternate CD comes with the same stuff that's on desktop except alternate CD uses text base installer instead of the GUI!  Either way, you will end up with the same stuff!

---

### Post by rekahsoft on 2006-08-17
ok...i will give that a try...then when i install it i will ```
sudo dpkg-reconfigure xserver-org
``` and report back.

---

### Post by taurus on 2006-08-17
> **rekahsoft said:**
> ok...i will give that a try...then when i install it i will ```
sudo dpkg-reconfigure xserver-org
``` and report back.

It should be

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by rekahsoft on 2006-08-17
ummm...not following????

---

### Post by taurus on 2006-08-17
> **rekahsoft said:**
> ummm...not following????
The last time I check, "sudo dpkg-reconfigure xserver-org" IS NOT the same as "sudo dpkg-reconfigure xserver-xorg"...  :rolleyes:

See a difference between those two commands!!!

---

### Post by rekahsoft on 2006-08-17
wow...srry i was tired...man that was stupid..my bad...regards :)

---

