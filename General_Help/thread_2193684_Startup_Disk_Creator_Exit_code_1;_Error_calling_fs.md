---
title: "Startup Disk Creator Exit code 1; Error calling fsync(2)"
date: 2013-12-14
forum: General Help
---

### Post by trevino.alan90 on 2013-12-14
I am getting this error when I am trying to create a 64 bit version live USB for my Macbook Pro on my Linux machine VIA Startup Disk Creator.

> org.freedesktop.UDisks.Error.Failed: Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdd: Input/output error


My system is Ubuntu 12.4 32-bit with 3G of ram. Technically speaking, this machine was made for XP Pro. I salvaged it from work. Lol!
The flash drive in question is a 16G Micro HCSD on a USB 2.0 converter. The Flash has been formatted on Ubuntu, and does read on the machine. I had also tried through a sandisk external card reader. 

Any ideas as to how I can get this ball rolling?


I have also tried creating the live USB on my Mac by going with the instructions on creating a **[dot] IMG **from a **[dot] ISO** file. That didn't work either.

EDIT: I'm sorry! The error was from FORMATTING my flash drive & creating the boot disk.

---

### Post by philinux on 2013-12-14
See this.

[http://askubuntu.com/questions/103953/cannot-format-500gb-usb-hd-cannot-create-partition-table](http://askubuntu.com/questions/103953/cannot-format-500gb-usb-hd-cannot-create-partition-table)

---

### Post by trevino.alan90 on 2013-12-14
This solved my problem! THANKS!!!

---

