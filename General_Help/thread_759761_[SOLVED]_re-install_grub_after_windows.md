---
title: "[SOLVED] re-install grub after windows"
date: 2008-04-19
forum: General Help
---

### Post by larsdk on 2008-04-19
I just re-installed my windows partition and obviusly that has removes GRUB in the MBR. Now I want to re-install using the liv-cd with the following instructions:

```

sudo grub

root (hd0,4)
setup (hd0,4)

```

which seems to be going fine (though it does compain about something with "embedding" - however it tells me that it shouldn't be an issue).

But when I reboot GRUB does not show up - how do I make it come back so I can boot into my Ubuntu?

Thanks for any help provided :)

---

### Post by the8thstar on 2008-04-19
Can you please elaborate?

Do you mean that you can't BOOT the computer or that you can't SEE Grub?

---

### Post by ibutho on 2008-04-19
One option is to use the [Super Grub Disk]("http://supergrub.forjamari.linex.org/"). Another option is to run the live cd, start gnome-terminal and do the following
```
sudo -s
mkdir /media/sda5
mount /dev/sda5 /media/sda5
chroot /media/sda5
grub-install /dev/sda
exit

```
The commands above assume that Linux is installed on /dev/sda5 (as indicated by hd0,4 in your post).

---

### Post by sandysandy on 2008-04-20
as suggested above u can fix MBR with an utility called Super Grub Disk ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/))

u can download it and burn it as iso image. then u can boot from the bootable CD and use the various options which r self explanatory. u can fix MBR of windows XP or Linux etc.

heres a tutorial on Super Grub.

[http://users.bigpond.net.au/hermanzo...bdiskpage.html](http://users.bigpond.net.au/hermanzo...bdiskpage.html)

regards

---

### Post by larsdk on 2008-04-20
the supergrub site seems to be down, but maybe I should give that a look.

Oh, and just to clarify the problem: I can boot, but it just boots directly into windows instead of displaying the options of menu.lst :confused:

---

### Post by forestpixie on 2008-04-20
New page apparently - didn't know either.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by larsdk on 2008-04-21
i just realized that the solution was to do 

setup (hd0)

instead of setup (hd0,4) while in grub :)

---

