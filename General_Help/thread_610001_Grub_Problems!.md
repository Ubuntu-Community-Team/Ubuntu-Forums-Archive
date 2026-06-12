---
title: "Grub Problems?!"
date: 2007-11-11
forum: General Help
---

### Post by Matoverton on 2007-11-11
I have a laptop which came with Windows Vista Home Premium pre-installed and I decided to put Ubuntu on it. Half a day later after hours of fruitless attempts to get it to connect to my Wireless Network, I became fed up.

I restarted, booted into windows, used the partition manager in Windows and simply deleted Ubuntu and used the free space left behind to expand the windows partition. 

Later after restarting, it attempts to load Grub, then stops and gives me Error 22 and doesn't let me continue. 

I searched on other forums and all of them pointed to me using a recovery tool on a disk for windows. The only difference is, my computer doesn't come with a disk, if windows becomes damaged you press F11 at startup and it boots from a seperate partition containing Windows recovery tools.

I tried doing this and to my complete and utter horror, it did nothing and grub tries to load anyway.

I have no disks, floppy or cds...
Help!...*sob*

---

### Post by shahein on 2007-11-11
Hi,

You need a windows cdrom, boot from it and then choose the 'repair' option afterwards type a dos shell

fixmbr

it worked for Windows Xp.

Regards.

---

