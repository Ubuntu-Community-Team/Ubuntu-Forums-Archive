---
title: "Wubi Not Starting after Installation"
date: 2008-06-07
forum: General Help
---

### Post by raziiq on 2008-06-07
I have installed the lastest Wubi 8.04 on my system which already contains Vista Home Japanese on C Drive and Vista Ultimate English on E Drive. My Wubi is installed on D drive which was empty before installing Wubi. I installed Wubi from my Vista Ultimate English.

Wubi installed successfully and asked me to reboot, when i rebooted my pc , and selected uBuntu from boot menu, the Beautiful uBuntu Loading window appeared after which a dos window appeared and performed several commands checking my hardware may be. But then it stuck at this command 
"Starting Common Unix Printing System: cupsd":(

what to do know , uBuntu is not working for me :(???

---

### Post by abn91c on 2008-06-07
If you have USB peripherals like printers attached remove them then try again

---

### Post by raziiq on 2008-06-08
I am using only USB mouse which i had already removed, also i turned off my Wifi Connection but still having problems starting uBuntu :(

I then booted into Windows Vista and used this Solution

[B]edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "all_generic_ide"
3. reboot
4. Ubuntu Install![/B]

Now when i rebooted my pc, i m getting different errors each time i restart my PC , sometimes its giving me devd-event[1609] and sometimes other errors.

Any Solutions, i m using Toshiba Laptop???

---

### Post by ago on 2008-06-09
boot in rescue mode (press esc at boot after ubuntu) 

what is the output of 

cat /proc/cmdline
dmesg

---

### Post by raziiq on 2008-06-09
thanks for the reply , i m sorry but i m a complete noob.

when i pressed Esc i got 5 options

Normal start
without graphics
Start for ACPI problem
Verbose
Live Cd Mode 

which option to select and how to enter this command?

Waiting for your kind reply

---

### Post by ago on 2008-06-09
try the acpi option first

---

### Post by raziiq on 2008-06-09
thanks for the reply , i ll check these commands in ACPI mode.
Are these two commands ??
[B]cat /proc/cmdline
dmesg[/B]

Also what are these commands for??

---

### Post by ago on 2008-06-10
They provide some useful info if you end up in a terminal

---

