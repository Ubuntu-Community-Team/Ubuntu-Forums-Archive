---
title: "[SOLVED] lirc &amp;amp; acpi_fakekey"
date: 2008-03-26
forum: General Help
---

### Post by realn on 2008-03-26
Hello,

 I have a IR receiver which I use witj lirc and dev/input driver. This basically registers as an input device. Now, I want to trigger special scripts through lirc+irexec.
I want to use acpi_fakekey in order to do KEY_VOLUMEUP, KEY_WHATEVER_I_WANT.
 The only problem "acpi_fakekey" doesn't work. It doesn't do anything. 
My question is :
sudo acpi_fakekey KEY_CODE 
is supposed to do anything on Kubuntu?
I saw some who say that they can print/trigger vents through acpi_fakekey, for some others it doesn't work?
Could someone point me to some directions? If I make acpi_fakekey work, then I hope I will be able to customize my remote control in any way I please.
If not, could someone point me to some source coe/programs which write directly to the kernel through /dev/uinput device.
Itried some, they don't seem to work either.

Thanks a bunch !!

---

### Post by realn on 2008-03-27
In fact the acpi-fakekey works wonderfully. Not for all the KEY_XXXX, but the most common ones are OK.
We can close the thread.

---

