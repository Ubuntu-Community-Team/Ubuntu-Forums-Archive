---
title: "Ubuntu 16.04 won't boot, screen flashes on startup, recovery mode files missing"
date: 2017-03-29
forum: General Help
---

### Post by lavieenroux on 2017-03-29
Hi all,

I have Ubuntu 16.04 dual-booting with Windows 7 on an old and rickety Samsung laptop. After messing around with some packages trying to get Caffe to compile, I attempted to reboot from the bootloader and the screen just flashes endlessly between a login screen, a loading screen, and a command line screen.

Went into recovery mode and tried to boot in failsafe graphic mode, but that just led to a black screen. Normal booting from recovery mode won't work either. When I try to repair broken packages, it attempts to install 10 new packages, including gcc 4.5, gcc 4.6, gcc 4.9, libhardware2, and libmedia1, which seems odd because I'm currently using gcc 5. The most concerning part is that it attempts to upgrade ~340 existing packages, including some important ones like language and keyboard packages, gnome, unity, and ubuntu (I assume these are all the ones that depend on gcc). In any case, I can't do the upgrade because the networking doesn't work either.

When I attempt to activate networking, I get the error that /etc/resolv.conf doesn't exist, which is just a link to /run/resolvconf/resolv.conf, which ALSO doesn't exist.

When I try to do a system summary, I get the error that the scaling_available_frequencies file doesn't exist, and the file in /lib/recovery_mode/options/system_summary tosses out something like the following error message: "arithmetic expression : expecting primary '/ 1000' "


I assume this has something to do with how, during my attempted Caffe installation, I switched to gcc 6 and then to gcc 5 and somehow messed everything up. Everything was booting fine before I attempted this boot. Does anybody have any insights on what I should try to fix this? Or should I do a complete reinstall of Ubuntu? I can still access all my files through the command line, it's just that the interface won't boot.

Thanks

---

