---
title: "Dual Boot linux"
date: 2007-05-28
forum: General Help
---

### Post by haplo_09 on 2007-05-28
HI I am pretty much new to linux. I install ubuntu dapper, (because 6.10 and 7.04) I simply could not get ati mobile x700 card to work. I want to install and try pc linux os without destroying dapper distribution ( I have some important softwre installed on it that I need for work). Do you know are there any guides that detaily explain how to dual boot second linux while having dapper already installed. I dont have windows installed. And my hard drive is partitioned into three parts ./ ./swap and leftover files from windows.

---

### Post by raul_ on 2007-05-28
Follow the same instructions you would follow for dual-booting with windows. It's all about creating a new partition and installing there. You don't need to create a swap partition, just use the one you already have. If you want you can also share your /home partition, but you need a new root partition

---

### Post by ajgreeny on 2007-05-28
If PCLinux installs its own grub, just be aware that it may or may not include an entry for ubuntu in the menu/lst file.  Ubuntu always finds other linux installs but many others don't.  If not don't panic.
In PCLinux open a root terminal and type:-
[B]mkdir /mnt/ubuntu
[/B]This makes a directory called /mnt/ubuntu then type:-
**mount /dev/hdXX /mnt/ubuntu/ -t ext3  **(hdXX will need to be changed to wherever your ubuntu is installed)
which will mount your ubuntu partition at /mnt/ubuntu.

Now using nautilus go to the ubuntu folder in /mnt/ubuntu and find the /boot/grub/menu.lst file.  Copy the entries for ubuntu from that and then add them to your PCLinux menu.lst file.  Now when you boot, still using the PCLinux grub, there will be an entry for ubuntu as well.

---

### Post by haplo_09 on 2007-05-28
Wow thanks folks. Another quick question do you have any good guide for dual boot dapper and windows?

---

### Post by ajgreeny on 2007-05-30
Great one here:-
[http://www.psychocats.net/ubuntu/installingdapperedgy](http://www.psychocats.net/ubuntu/installingdapperedgy)

---

