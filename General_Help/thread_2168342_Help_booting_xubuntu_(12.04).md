---
title: "Help booting xubuntu (12.04)"
date: 2013-08-17
forum: General Help
---

### Post by tochimclaren on 2013-08-17
i actually switched laptod off
myself, before this began
popping on my screen. And i
have only xubuntu installed in
the laptop. (No dual boot) mount: mounting /dev/disk/by-
uuid/0655797a-fbcd-4cea-8779-
a201878442ff on /root
failed:invalid argument
mount: mounting /dev on /root/
dev failed: No such file or directory
mount: mounting /sys on /root/
sys failed: No such file or
directory
mount: mounting /proc on /root/
proc failed: No such file or directory
target filesystem doesn't have
requested /sbin/init.
No init found. Try passing init=
bootarg. BusyBox v1.18.5 (ubuntu
1:1.18.5-1ubuntu4.1) built-in shell
(ash)
Enter 'help' for a list of built-in
comands. (iniframfs)
now thats were am stuck, i've
read other article were people
have this same problem, it is
usually caused by dual booting, but am not dual booting.
And i have another problem my dvd/cd drive is busted and i
can't boot from usb.
All am asking is, is there
anyway i can solve the issue
without live cd?

---

### Post by ibjsb4 on 2013-08-17
Can you get to a terminal or tty?

[http://ubuntuforums.org/showthread.php?t=915095&p=5775963&viewfull=1#post5775963](http://ubuntuforums.org/showthread.php?t=915095&p=5775963&viewfull=1#post5775963)

If you can't, then I don't know what to tell you :(

---

### Post by EvilLugiaXD on 2013-08-17
This sounds exactly like my problem. I am on ubuntu 12.04 and only have this stalled into my computer. Except the commands won't work or anything. I have a feeling this is a type of virus.

---

### Post by tochimclaren on 2013-10-06
how do i get to terminal? I switch my laptop on and loads like... Forever then drops me in the busybox.

---

### Post by tochimclaren on 2013-10-14
when i typed dmesg |tail
this what i get
[35.404915] Descriptor sense data with sense descriptors (in hex) :
[35.404972]        72 03 11 00 00 00 0c 00 0a 80 00 00 00 00 00
[35.405345]         01 05 a9 e4
[35.405477] sd 0:0:0:0: [sda] add. Sense: unrecovered read error - auto reallocate failed
[35.405572] sd 0:0:0:0 [sda] CDB: Read(10): 28 00 01 05 a9 68 00 00 f0 00
[35.405870] end_request: I/0 error, dev sda, sector 17148388
[35.405941] ata1: EH complete
[35.406025] JDB2: Failed to read block at offset 13378
[35.406079] JDB2 recovery failed
[35.406116] EXT4-fs (sda1): error loading jornal
(iniframf) 
please i need help

---

