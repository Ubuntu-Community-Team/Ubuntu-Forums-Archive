---
title: "Ubuntu only boots with usb plugged in"
date: 2016-09-18
forum: General Help
---

### Post by robweps2 on 2016-09-18
I just installed Ubuntu-16.04.1-server-amd64. Installation went fine. Then I removed the USB-key, the computer restarts with Ubuntu. I can see that Ubuntu is booting. It goes very fast, but I can see that about 2 pages of commands are coming by. But then the computer suddenly reboots.
After the reboot it shows me the Grub-menu, when I just press Enter, Ubuntu starts booting again, but only when I have the USB-key plugged in.

Edit: I just found out that it doesn't have to be the USB-key. I added another harddrive. And that is also OK.

So it's not a problem of booting from the wrong device as I have disabled in my bios the option to boot from USB. I have set that the only available bootdevice is my harddrive (SSD).

Just to be sure I entered the following commands:
sudu install-grub /dev/sda
sudo update-grub

[http://paste.ubuntu.com/23196669/](http://paste.ubuntu.com/23196669/)

---

### Post by sudodus on 2016-09-18
Welcome to the Ubuntu Forums :-)

I think the file 'sda1/boot/grub/menu.lst' is an old file, that belongs to previous versions of grub. Maybe it is causing confusion.

This is also how I interpret the suggested repair:

> =================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to fix legacy files) and reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


---

### Post by robweps2 on 2016-09-18
When I try the default repair, the repair program hangs on: Purge kernels then reinstall last kernel sda1 (ins). This may....
After reboot I have an empty grub (I think). I get some command-line grub interface.

But are there 2 different boot procedures? Why does the first boot reboots and does the 2nd boot completes?

---

### Post by sudodus on 2016-09-18
Purge kernels then reinstall last kernel can take a very long time. Maybe it did not hang, but was still working. Try again and give it more time. After that, please run the BootInfo script again and post a link to the result.

There are other people around, who know better how to read the BootInfo, and with the new data, I think they will chip in and help :-)

---

### Post by robweps2 on 2016-09-18
It's solved. I did some Magic here and there :-\" and then a little apt update && apt upgrade ](*,)

Thanks.

---

### Post by sudodus on 2016-09-18
Congratulations :KS

In order to help other users, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

