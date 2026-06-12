---
title: "Single Boot-Loader for Ubuntu, Windows XP x86 and Windows XP x64?"
date: 2007-01-17
forum: General Help
---

### Post by t_anjan on 2007-01-17
I have Ubuntu, Windows XP Media Center Edition, Windows Server 2003 and Windows XP x64 installed.

The 3 windows OSs use the Windows Boot loader.

When I power on my computer, I'm first shown the GRUB loader with a few options for Ubuntu, and just one other option for Windows. When I select the Windows option, I'm then shown the Windows Boot-loader.

Is there any way to integrate the two loaders? I want to show all the OSs using a single menu. Is this possible?

---

### Post by Ramses de Norre on 2007-01-17
You can edit the windows bootloader to automaticaly boot windows without a menu and then put the window entries in grub.
In grub it's as easy as this: ```
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

And you just have to fill in the right partition on the root line for each install and give them an appropriate title.

For editing the windows bootloader: try msconfig (start > run) and look if you can find it in their, otherwise try google (I haven't used windows for a while so I'm not sure where it is).

---

### Post by t_anjan on 2007-03-18
Thank you for your reply. I've got a working single menu boot loader now, but it was a slightly more complicated process because I installed Vista recently.

---

