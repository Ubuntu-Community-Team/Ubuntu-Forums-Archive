---
title: "Error installing kernel in 64-bit Ubuntu"
date: 2008-06-06
forum: General Help
---

### Post by dlmoak on 2008-06-06
I'm trying to install 2.6.24-18-generic.
Ran the following code:
sudo apt-get update
sudo apt-get install linux-image-2.6.24-18-generic

- seemed to get the updates but when I tried to run the install I got this message:
E: Couldn't find package linux-image-2.6.24-18-generic

I'm running 64-bit Ubuntu - what do I need to do?

---

### Post by Thanoulis on 2008-06-06
I also run a Ubuntu 8.04 - 64bit:
With a: 
```
sudo apt-get upgrade
```
you'll get the .18 kernel as it is the default kernel version from now on...

---

### Post by dlmoak on 2008-06-06
Thanks - I'll try it out when I get home and let yo know what happens.

---

### Post by dlmoak on 2008-06-06
I ran

sudo apt-get upgrade

and got this response:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What next?

---

### Post by dlmoak on 2008-06-06
Ran the following code and the kernel installed:

sudo apt-get install linux-image-2.6.24-18-generic

Thanks for everyone's help.

---

