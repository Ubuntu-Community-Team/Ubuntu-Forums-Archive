---
title: "nVidia drives prevent system boot"
date: 2017-08-31
forum: General Help
---

### Post by Hasimir on 2017-08-31
Help!
I was following the instructions from this website ( [http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux](http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux) ).
All went fine until the moment of reboot.
The computer turned off.
Then turned on.
It got past grub, initialising the Linux boot (I am now writing from the secondary Windows partition).
Started scrolling weird text on screen (a pretty normal thing).
And then stopped.
No new text appear on screen, and instead the screen keeps blinking on and off.

What can I do? T_T

---

### Post by Autodave on 2017-08-31
According to Nvidia's website, 384.69 is the driver that you should be using. Do you know what one you actually installed?

In the future, the safest way to install a Nvidia driver is to go to Settings -> Additional Drivers, and then install the recommended one.

---

### Post by Hasimir on 2017-08-31
Crisis averted.
I managed to boot in Recovery Mode, from there I accessed the Root shell and did a purge of the offending nVidia material. This allowed the system to reboot using the Nouveau drivers.

About the nVidia drivers themselves, they were indeed the 384.69 version o_O
I'll try again now, but going through the Additional Drivers panel >__<

Thanks

---

