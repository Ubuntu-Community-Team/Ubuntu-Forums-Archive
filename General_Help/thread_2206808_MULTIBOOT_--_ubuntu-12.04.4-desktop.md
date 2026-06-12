---
title: "MULTIBOOT -- ubuntu-12.04.4-desktop"
date: 2014-02-20
forum: General Help
---

### Post by pendulous on 2014-02-20
Sitting here running parted magic on USB since both my OS drives failed and waiting on the RMA drives to be delivered in a few days.

What I'm attempting to do is install Ubuntu (ubuntu-12.04.4-desktop-amd64.iso) on the USB drive, from within parted magic.

Unfortunately, the multiboot USB was created with YUMI under windows, and there seems to be no YUMI package for parted magic, so that I can execute YUMI, add the iso and let it run the scripts to install as it usually would. BUT.... I'm left with manually configuring the scripts that are already on the USB drive. Question is, how can I add Ubuntu to the YUMI USB drive and boot directly from the iso?

1. Added ubuntu-12.04.4-desktop-amd64.iso to media/sdc1/multiboot/ISOS
2. Added text (ubuntu-12.04.4-desktop-amd64) to /media/sdc1/multiboot/Installed.txt
3. Added folder Ubuntu (/media/sdc1/multiboot/)
4. Added folder YUMI (/media/sdc1/multiboot/Ubuntu/)
5. Added text file menu.lst (/media/sdc1/multiboot/Ubuntu/YUMI) :
```
# This Menu created with YUMI (Your Universal Multiboot Installer) http://www.pendrivelinux.com
default 1
timeout 30
color NORMAL HIGHLIGHT HELPTEXT HEADING
splashimage=/multiboot/menu/yumi.xpm.gz
foreground=FFFFFF
background=000000

title --- Directly Bootable ISOs + Windows XP ---
root

title <-- Back to Main Menu
root (hd0,0)
chainloader (hd0)+1
rootnoverify (hd0)
```

6. Added appended text in /media/sdc1/multiboot/menu/menu.lst :
```
#start Ubuntu
#Modify the following entry if it does not boot
title Boot acronis.iso from Memory
find --set-root --ignore-floppies --ignore-cd /multiboot/ISOS/ubuntu-12.04.4-desktop-amd64.iso
map --heads=0 --sectors-per-track=0 --mem /multiboot/ISOS/ubuntu-12.04.4-desktop-amd64.iso (hd32)
map --hook
chainloader (hd32)
#end Ubuntu

```

But system doesn't load... says incorrect chainloader, invalid or unsupported  executable format or something.


Is there a simpler way to doing this? Am I doing this correctly?

---

### Post by pendulous on 2014-02-21
Solved.

---

### Post by deadflowr on 2014-02-21
> **pendulous said:**
> Solved.

Solved with magic?

You had an interesting dilemma, would you care to post how you fixed it?

---

### Post by pendulous on 2014-02-21
> **deadflowr said:**
> Solved with magic?

You had an interesting dilemma, would you care to post how you fixed it?

Yes, pretty much magic! 

I cheated!! Forgot I had F4UBCD setup on the usb and booted into there, ran yumi within minixp to do all the work.

---

