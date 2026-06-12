---
title: "Computer refuses to shut down"
date: 2015-04-19
forum: General Help
---

### Post by fkervin on 2015-04-19
Hi All,

I've a computer using xubuntu and refuses to shutdown or restart, it gets hanged and I've to press reset or power button.

I've press "F1" key when power off and those are the last lines before it gets frozen:

```
nm-dispatcher.action: Disconnected from the system bus, exiting.
*deactivating swap...
*unmounting local filesystems...
*Will now halt
[   24.464703] reboot: Power Down 
```

Any help about how to make it restart correctly?

Regards and many thanks in advance

---

### Post by kc1di on 2015-04-19
You can try this in a terminal ```
gksu mousepad
```  Not sure if it's mousepad or leafpad in xubuntu but in any event bring up a text editor of your choice with root priviledges. then open /etc/default/grub file and edit it so that the line that looks like this

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Looks Like this instead:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force "
```

Save the file then in a terminal type ```
sudo update-grub
```

When it's finished try to reboot  and then try a shutdown see if it works.
Good luck

---

### Post by fkervin on 2015-04-19
Many thanks Kc1di,

Default text editor in Xubuntu is mousepad :). I've done it but problem unfortunately remains :(

If you've another idea....

Many thanks and regards

---

### Post by kc1di on 2015-04-19
Give us a little more Info on the machine . 
How old, Video card, ram CPU Etc if you know.

---

### Post by fkervin on 2015-04-19
Hi again, kc1di,


Computer is a G3240 intel APU using its integrated graphics card, 4GB RAM, SSD as system disk and mechanical disk for storage. Mainboard is an H81 or similar (I'm not at this moment in this computer). The computer is new.

Regards

---

### Post by fkervin on 2015-04-19
Hi again, kc1di,

If I disable the option "USB Remote/Keyboard power on" on BIOS the problem is solved but then I can't power on the computer with the keyboard, that is something very desirable.

I'm check the BIOS version for the motherboard but there is no update available (I have latests version).

Im other motherboards I've enable this BIOS option having no problem.

Regards

---

### Post by kc1di on 2015-04-19
Sorry I can't be of much Help to you on this one as I've never Had that problem here.  Hope someone will come along and be of assistance to you soon. 
Is it a wireless keyboard of wired?  You might try a wired one if it's wireless see if that works.

---

