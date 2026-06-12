---
title: "Graphic Card Issue with Ubuntu [Skylake GT2 520, DRM-i915)"
date: 2023-07-24
forum: General Help
---

### Post by adedamolaxl on 2023-07-24
im having a problem with my linux OS(ubuntu), when i boot into it, i run  into screen freeze/blank screen issues. 

i have noted that this is a graphic card issue, as when i boot into  recovery mode the OS works due to the disabled graphic driver. 

i also run a dual boot system, so when i run windows OS, there is no  problem at all.

 i recently tried reinstalling another linux OS(fedora) and the screen  froze again! just before i started installation

my graphic card driver is Intel SKylake GT2 520.

i have seen errors related to drm-i915 being incompatible with the newer kernel versions

but even when i use 5.19 which is the recommended i run into the same issue.

the only temporary respite was when i switched from wayland to xorg but the problem has returned again

iam currently working on recovery moe.  this problem is tiring. i need help!

---

### Post by Bashing-om on 2023-07-24
adedamolaxl - Hello

Please post back - between code tags - the outputs of terminal commands:
```

lsb_release -a
lspci -k | grep -iEA5 'vga|3d'

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

So we know exactly what we are working with.

[INDENT]all in the process
[/INDENT]

---

### Post by MAFoElffen on 2023-07-25
Lets speed up the fact-finding process, and get into the resolution process: Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and post the URL of where the report uploads to a pastebin.

That will show us what hardware you are running, which graphics engine, graphics driver, ad graphics environment settings... as well as the kernel version.

I am fairly sure that adding one or two boot parameters may help you, but I need to see what hardware, kernel, and other settings are there in place first.

---

