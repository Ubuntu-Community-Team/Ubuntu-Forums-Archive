---
title: "how to change drive (ie: c: in dos)"
date: 2008-02-26
forum: General Help
---

### Post by walter_j on 2008-02-26
my mbr may be corrupt, so i booted from ubuntu livecd to delete the files in /boot/grub so that i can reinstall grub, i can't find how to change to the hard drive when i booted from the livecd. i tried deleting the files from the file browser in the livecd, but i don't have permission to do this. so in short, i want to do the following...

1. from the live cd, change to my fixed disk, which is listed as /dev/sda1 in fstab
2. copy /boot/grub/menu.list to my home directory /home/walter
3. erase files in /boot/grub
4. copy menu.list from my home directory to /boot/grub (ii only have one hard disk - is this necessary?)
5. reinstall grub using super grub

i tried using super grub without all this rigermarole but no go.

---

### Post by pytheas22 on 2008-02-26
You need to mount your hard disk first.  From the live session:
```

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```

Then cd to /media/sda1 and you will see your file system.

But a bigger question is, why do you think grub is corrupted?  Maybe you have a good reason for this, but if I were you, I would make sure that that's indeed the problem before trying to reinstall grub, which can cause a lot of problems, particularly if you have a dual-boot system.

---

### Post by walter_j on 2008-02-26
when booting i get stage1.5 and then get error 15. i followed instructions on how to fix grub  from other posts here, and i get success message, but when i reboot, i get error 15 again. i used supergrub to fix grub, and got success message, but still won't boot. a post somewhere with same problem suggested that files may be corrupt in grub, and to delete the files and reinstall grub.

i'm open to other suggestions. reinstall kubuntu maybe? can i reinstall without losing all my data and programs?

i only have one hd, and am only running kubuntu 7.10

no idea why grub got messed up. the hd is only a few months old. i was messing with compiz, but was getting video problems with my ati 9200se card, so shut down, then got error 15 when rebooting.

---

### Post by pytheas22 on 2008-02-26
If your whole Ubuntu system is installed on one partition (which it appears to be, since sda1 is the only partition in /dev), then you would lose all of the data on it with a reinstall.  If you had set up /home on a separate partition, you could reinstall the system without losing your personal files--this is good to keep in mind for the future.

Anyway, if you can't afford to lose your data (you could always copy it over to other media by using the live CD and mounting the hard disk as I outlined in my first post), then I guess that reinstalling grub is the best thing to do.

First though, it might not hurt to make sure that the drive cable is connected firmly to your motherboard, and turn on SMART in BIOS to see if it gives you any warnings.  If you have a second graphics card in addition to your ATI device, you could also try unplugging the ATI card and booting using the secondary one, in case the ATI card is the source of the problem (not likely, but you do mention that you made changes to it before the problem started).

Another thing to consider is using the program testdisk, which is supposed to be able to detect bad MBR's and repair them (I've never used it for this purpose but I've done other stuff with it and it's very good).  You would need to find a live CD that comes with testdisk installed and boot to it--I think that RIP Linux, [http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/) includes it.

EDIT: I recall that testdisk is also in the Ubuntu repositories, so if you have Internet access from your live session, you could install testdisk via Synaptic that way; no need to burn a separate CD.

---

### Post by oldos2er on 2008-02-26
Usually grub error 15 means there's a typo or other error in your "kernel /boot" line. See [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

 You shouldn't need to reinstall.

---

