---
title: "Cannot load btsco module"
date: 2005-07-30
forum: General Help
---

### Post by liraz on 2005-07-30
I have compiled the bluetooth alsa module succesfully - [http://sourceforge.net/projects/bluetooth-alsa/](http://sourceforge.net/projects/bluetooth-alsa/). All instructions followed, no errors.

When trying to load snd_bt_sco I get the following:

> 
root@ubuntu-9njaoje:~# modprobe snd_bt_sco
FATAL: Module snd_bt_sco not found.


The module does exist, so I tried giving it the direct link to the module:

> 
root@ubuntu-9njaoje:~# modprobe /lib/modules/2.6.10/extra/snd-bt-sco.ko
FATAL: Module /lib/modules/2.6.10/extra/snd_bt_sco.ko not found.


Ok it should be noted, my kernel is actually in /lib/modules/2.6.10-5-686-smp. I dont understand why the module was sent to 2.6.10. I'm fairly new to linux and am so far finding it quite difficult to get many small thigns working.

Please, I have no idea what this could possible be.

---

### Post by Xian on 2005-07-30
Do you have the linux-headers package installed for your kernel type?

---

### Post by liraz on 2005-07-30
Yes. linux-headers-2.6.10-5-686-smp.

---

### Post by liraz on 2005-07-31
I am unsure, but perhaps in ubuntu I need to specify which kernel-headers to compile against? 

Or should this be done automatically(as was done in fedora) by what kernel is currently being used?

---

### Post by ManOwaR on 2005-10-11
...i have the exact problem on kernel 2.6.10-5-686.

and my question is, why modprobe can't find the module even though it's there.

---

### Post by reto on 2005-11-23
I had the same error message because I had the btsco module that cames with breezy loaded, after removing it snd_bt_sco loads succesfully (I did move it into the directory where the other modules are, for me /lib/modules/2.6.12-9-686/extra/ rather than /lib/modules/2.6.12-9/extra/ where the make-script put it).

---

