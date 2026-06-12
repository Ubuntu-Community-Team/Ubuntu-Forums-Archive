---
title: "X crashes after software update"
date: 2007-11-27
forum: General Help
---

### Post by torrent478 on 2007-11-27
Hi there,

I have been using my laptop with 7.04 feisty for a while now, without running into something I couldnt fix myself before, but this problem is totally stumping me.

After doing a standard software update and restarting X crashes and I get this error:

(==)Log file: "/var/log/Xorg.0.log", (date)
(==) Using config file: " /etc/X11/xorg.conf"
FATAL: Couldnt not open
  ' /lib/modules/2.6.20-16-lowlatency/volatile/nvidia.ko' : no such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE)NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found


Every once in a while when I do an update my sound will die but i can fix that through re-compiling the alsa drivers usually, but now that im in terminal with no X im really not sure what to do. 

any help would be great, i really need this up and running fast because i take all my notes for school on this laptop and finals are coming up fast!

---

### Post by FuturePilot on 2007-11-27
How did you install the Nvidia driver? Looks like a problem with that.

---

### Post by torrent478 on 2007-11-27
I installed them a long time ago with envy

---

### Post by FuturePilot on 2007-11-27
> **torrent478 said:**
> I installed them a long time ago with envy

Try reinstalling them with Envy. You can do it from the command line like so
```
sudo envy -t
```

---

### Post by torrent478 on 2007-11-27
it worked thanks :grin:

you really saved me I have class in the morning and need this to take notes

hehe you dont know how much I appreciate this \\:D/

---

### Post by FuturePilot on 2007-11-27
No problem :)
I'm guessing the kernel may have been updated. And when you manually install the Nvidia driver or use Envy, X breaks when the kernel gets updated due to the Nvidia kernel module being built against the older kernel. So then it ends of with module mismatches and X breaks. Simply you just have to rerun Envy again to rebuild it against the newer kernel.

---

