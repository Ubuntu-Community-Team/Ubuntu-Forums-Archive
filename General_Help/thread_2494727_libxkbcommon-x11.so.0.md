---
title: "libxkbcommon-x11.so.0"
date: 2024-01-25
forum: General Help
---

### Post by centguy2 on 2024-01-25
My system has a lot of missing shared objects such 
as 

```

libX11.so.6 => /lib/x86_64-linux-gnu/libX11.so.6 (0x00007fc0116c0000)
    libxkbcommon-x11.so.0 => not found
    libxkbcommon.so.0 => not found
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fc0121bc000)
    libstdc++.so.6 => /lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fc0109d4000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fc0108ed000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fc01219c000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fc0106c4000)
    libxkbcommon-x11.so.0 => not found
    libxkbcommon.so.0 => not found


```


Instead of hunting down each one to install, what is the best apt install command that can magically bring down all this?

---

### Post by ajgreeny on 2024-01-25
We know nothing about your system at the moment so it's impossible to give you much help.

Please tell us in as much detail as possible your version of Ubuntu and your hardware, preferably by running command
**inxi -Fzx**
and then post back here the output using code tags please.
See my signature below for a **How To** for code tags

---

### Post by Rubi1200 on 2024-01-25
It would also be helpful if we knew what commands you were running to discover these missing elements and why you were running them.

Info asked for by **ajgreeny **is essential to offer help.

---

