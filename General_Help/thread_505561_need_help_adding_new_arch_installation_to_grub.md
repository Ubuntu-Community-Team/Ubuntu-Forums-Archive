---
title: "need help adding new arch installation to grub"
date: 2007-07-20
forum: General Help
---

### Post by TheRingmaster on 2007-07-20
Hi,

I just installed arch linux on my computer. First I make a space for it with gparted, then I installed arch on the free space I just made, and now I must edit grub so that it gives me a choice of ubuntu or arch when I start up the computer. I have really no knowledge of how to do this. If someone could help me in this manner, that would be great!

---

### Post by confused57 on 2007-07-20
> **TheRingmaster said:**
> Hi,

I just installed arch linux on my computer. First I make a space for it with gparted, then I installed arch on the free space I just made, and now I must edit grub so that it gives me a choice of ubuntu or arch when I start up the computer. I have really no knowledge of how to do this. If someone could help me in this manner, that would be great!

You might be able to set up grub using one of these methods:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

I'm not familiar with arch linux, so I can't give you specific advice for this distro...if it uses grub, you might consider using a configfile entry....you need to adjust the entry, if arch linux uses grub.conf, instead of menu.lst.

---

### Post by TheRingmaster on 2007-07-20
some additional information,

My arch installation is located at /dev/hda3. ubuntu is at /dev/hda1 (fyi)

---

### Post by confused57 on 2007-07-20
> **TheRingmaster said:**
> some additional information,

My arch installation is located at /dev/hda3. ubuntu is at /dev/hda1 (fyi)
First of all, you want Ubuntu's grub installed to the mbr...if it isn't, use the live cd to install it on the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then to edit your menu.lst to boot arch linux:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add an entry something like this to the very end of your menu.lst to boot arch linux:
```
title        Arch Linux on /dev/hda3
configfile   (hd0,2)/boot/grub/grub.conf
```

quit & save

If this doesn't work try "configfile (hd0,2) /boot/grub/menu.lst[/code]

---

### Post by el mariachi on 2007-11-25
I tried this but it returns an error:
"Bad filename (must be absolute pathname or blocklist)"

Arch is on SDB3, so (hd1,2) right?
```
title  Arch Linux
configfile	(hd1,2) /boot/grub/menu.lst
``` isn't this right?

---

### Post by confused57 on 2007-11-25
> **el mariachi said:**
> I tried this but it returns an error:
"Bad filename (must be absolute pathname or blocklist)"

Arch is on SDB3, so (hd1,2) right?
```
title  Arch Linux
configfile	(hd1,2) /boot/grub/menu.lst
``` isn't this right?

There's no space between (hd1,2) and /boot/grub/menu.lst:

should be:
```
title  Arch Linux
configfile	(hd1,2)/boot/grub/menu.lst
```

---

