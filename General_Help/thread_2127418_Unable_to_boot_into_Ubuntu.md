---
title: "Unable to boot into Ubuntu"
date: 2013-03-20
forum: General Help
---

### Post by Mahrio on 2013-03-20
Hi guys, so heres a little back-story. I dualboot windows 8 and ubuntu 12.10. I use two partition on the same HDD. My ubuntu partition was starting to run low on memory, so i added ten gigs to it. Now it wont boot in to ubuntu, it says: Error no such devie : 7802EDF027EA234. so then i decided to restart my computer and select "Advanced boot options" or the option that's something like that, and i selected the option with "(recovery)" beside it. then a bunch of text came on my screen, i let it do it's thing, then i got the message: Alert! /dev/disk/by-uuid/7802EDF027EA234 does not exist [COLOR=#000000][FONT=Ubuntu Mono]Dropping to a shell! (ash)

So yeah, you guys have any advice? I'm a complete noob to ubunutu. I read some stuff about grub, and checked my grub folder from windows 8 and it's empty.

Any and all help appreciated, Thanks guys! :)
-Kind Regards[/FONT][/COLOR]

---

### Post by dino99 on 2013-03-20
each time a partition is modified (resized for example, or moved) a new uuid is created but the grub menu need to be updated to know about that new uuid. Thats why you get that error "no such device"

so from the shell, run the commands:
- sudo grub-install /dev/sda
- sudo update-grub

then reboot normally, that problem should be gone  ):P

---

### Post by Mahrio on 2013-03-20
hey, dino,thanks for the reply.
i apologize for my inexperience, where do I type it? where is "the shell?" 
thanks for all the help

---

### Post by engineerarun on 2013-03-20
Does this help?
[http://opensource-sidh.blogspot.in/2011/05/install-grub-in-ubuntu-from-server-cd.html](http://opensource-sidh.blogspot.in/2011/05/install-grub-in-ubuntu-from-server-cd.html)

---

### Post by Mahrio on 2013-03-20
I dont think the grub files are missing :/

---

### Post by Mahrio on 2013-03-20
bump, please help someone. i tried using boot repair by booting into ubuntu using a usb and it gave me the url "past.ubuntu.com/5631570"
help please

---

### Post by Mahrio on 2013-03-21
plaes? :(

---

