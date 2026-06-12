---
title: "Installing amp module into the kernal"
date: 2005-04-28
forum: General Help
---

### Post by tara_zw on 2005-04-28
Hi

Linux newbie (of note :-)).

Having a suspend (and hibernate problem) think I may need to install amp into my kernal......does anyone know how I should go about doing this? And if so please may i have detailed newbie instructions? Don't be afraid to patronise - I know nothing!

Tara :-)

---

### Post by az on 2005-04-28
Do you mean apm?

'Cuz I googled for amp and found this:
[http://www.cs.berkeley.edu/~zf/amp/](http://www.cs.berkeley.edu/~zf/amp/)
I dunno what that is, but that does not mean much...

If you have an older computer that does not use acpi, you need apm to do suspend-to-ram and poweroff properly.

Try installing apmd using synaptic.  Also, load the apm module
sudo modprobe apm.

If that makes your motherboard happy, add the word "apm" to the bottom of the /etc/modules file.  That will make the module load on boot.

sudo gedit /etc/modules

---

### Post by tara_zw on 2005-05-02
Sorry did mean apm!

I checked for it in synaptic and re-installed it (as was installed already). The attempted to add it to the module as advised (through the terminal?) and got this responce:

FATAL: Error inserting apm (/lib/modules/2.6.10-5-686/kernel/arch/i386/kernel/apm.ko): No such device


any suggestions?

xox

---

### Post by crypticreign on 2005-07-14
This is what got apmd working for me on my Dell Inspiron 5000:

Edit '/etc/modules/' and add the following line:
apm

Edit '/boot/grub/menu.list' and add the following to your 'kernel' option:
acpi=off apm=on



Also you could build a custom kernel and enable apm (perhaps that is a reason for the )

Here is a HowTo on how to build a custom kernel, it's really simple - [https://wiki.ubuntu.com//KernelCompileHowto](https://wiki.ubuntu.com//KernelCompileHowto)

---

