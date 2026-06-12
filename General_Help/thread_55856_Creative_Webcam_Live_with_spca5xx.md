---
title: "Creative Webcam Live with spca5xx"
date: 2005-08-10
forum: General Help
---

### Post by einKI on 2005-08-10
Hi

i try to get my Webcam running under ubuntu.
I downloaded the latest version of the spca5xx  driver 
installed from synaptic the linux-headers-2.6.10-5
made a link to these headers
ln -s /usr/src/linux-headers-2.6.10-5  /lib/modules/2.6.10-5-386/build 

compiled the driver as described in th readme
make clean
make 
make install

But now when i want to load the driver with modprobe spca5xx i get
FATAL: Error inserting spca5xx (/lib/modules/2.6.10-5-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

dmesg says
spca5xx: version magic '2.6.10-5 SMP preempt PENTIUM4 4KSTACKS gcc-3.3' should be '2.6.10-5-386 preempt 386 gcc-3.3'

I dont know why it doesnt work i have tried some hints from other posts but i have made none of the mistakes described there

thx
einKI

---

### Post by az on 2005-08-10
What version of linux-headers do you have installed?

It should be 2.6.10-5-386

and not SMP.

---

### Post by einKI on 2005-08-11
Hi

I installed 
linux-headers-2.6.10-5-i386 which installed autmatically linux-headers-2.6.10-5
i thought therefore both are the same until I realized that there are not only links to the -i386 kernel but some other files.

After i corrected the link althing works perfect

thx

---

