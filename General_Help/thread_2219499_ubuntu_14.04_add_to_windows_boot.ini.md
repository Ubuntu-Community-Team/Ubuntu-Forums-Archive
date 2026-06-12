---
title: "ubuntu 14.04 add to windows boot.ini?"
date: 2014-04-24
forum: General Help
---

### Post by jhay2 on 2014-04-24
hi , is it possible to add ubuntu 14.04 partition on windows bootloader (Boot.ini)

my ubuntu 14.04 installed at sda1 and my windows installed at sda2 , i want to use windows bootloader instead of grub .. 

any reply are much appreciated thank you :)

---

### Post by keithcleaver2010 on 2014-04-24
AFAIK, you can't use the windows boot loader to load a linux partition. The vast majority of distros use Grub as the boot loader.

You can however, edit grub to include both your Linux & Windows partitions, and if you wish to set your windows partition as your default, you can do that too.

---

