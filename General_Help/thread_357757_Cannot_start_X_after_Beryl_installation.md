---
title: "Cannot start X after Beryl installation"
date: 2007-02-10
forum: General Help
---

### Post by ekuliak on 2007-02-10
Ok, so here's my problem:

I was installing Beryl on my dad's computer, because he wanted the eye-candy (I have it running on my computer with Kubuntu, while I installed Ubuntu on his).  
I used [this guide]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA").  I did the script install.

Everything seemed to go ok, Beryl was up and running, and I had wobbly windows.  But then I noticed that in his system tray was an icon telling me a reboot was necessary.  So I rebooted.

After that, X wouldn't start up anymore!  Even restoring the old xorg.conf backup file wasn't working.

I keep getting some error like: "API Mismatch NVIDIA kernel module has version 1.0-7184 but this X module has the version 1.0-9746"

How can I fix this API mismatch?

---

### Post by bustanil on 2007-02-10
Reinstall your nvidia driver using this version [http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html).

---

### Post by ekuliak on 2007-02-11
I tried doing that, but it still didn't work.


I just set it to boot into an older kernel version, for now.  Only issue (as far as I know) is that some windows just turn black after a while when using Beryl.

---

### Post by Mba7eth on 2007-02-12
remove all nvidia and beryl packages. Install nvidia again with envy or from official site. Then try beryl. Have faced the same problem.

---

