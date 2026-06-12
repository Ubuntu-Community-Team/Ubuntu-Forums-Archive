---
title: "Some Wine problems"
date: 2007-08-04
forum: General Help
---

### Post by GeneralHooHa on 2007-08-04
I was trying to install battlefield 2142 with wine. The setup finished, but it failed to install directx. After searching for a while, I got to this HOWTO:

[http://ubuntuforums.org/showthread.php?t=29996&highlight=cedega+cvs]("http://ubuntuforums.org/showthread.php?t=29996&highlight=cedega+cvs")

Well, I did everything on there, and I had a few errors along the way (can't remember them), but I ignored them and kept following the instructions. Eventually, when I got to winetools I had more errors. So I uninstalled everything and started from scratch... well I thought I did.

Now, when I try to run the setup.exe from  the CD I get an "Error: -6006" on the windows installation manager. I don't think I completely uninstalled wine cvs or winetools, and don't know how. How can I  remove everything "wine" and start from scratch?

---

### Post by GeneralHooHa on 2007-08-04
If I type "sudo wine /media/cdrom0/setup.exe" it goes starts to load the install screen, and then  freezes the program. I get this output:
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
nick@[private]-Laptop:/media/cdrom0$ fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x30054
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x30054

```

---

### Post by machoo02 on 2007-08-04
to remove your fake C: drive and start over, enter this in the terminal:```
rm -r ~/.wine
```

Then, to re-create a new fake C: drive, enter ```
winecfg
```.

Be sure to check out the [WINE application database]("http://appdb.winehq.org") for your program to see if there are any tips/tricks.

---

