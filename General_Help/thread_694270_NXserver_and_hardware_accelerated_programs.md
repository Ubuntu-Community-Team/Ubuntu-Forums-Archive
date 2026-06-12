---
title: "NXserver and hardware accelerated programs"
date: 2008-02-11
forum: General Help
---

### Post by karatefish on 2008-02-11
Hi all,

I've installed the NX server free edition on my computer, and it works really well so far. It doesn't seem to do hardware acceleration, so I'm using it to connect to the local X session. After disabling desktop effects, it works fine, except that accelerated programs don't refresh properly.

I can use standard programs ok, but when I start a vmplayer virtual machine with hardware accelerated graphics, the virtual machine window only refreshes if I cover it with another program and then bring it forward again.

I can use x11vnc (or connect to a vnc session with nx), which shows the virtual machine without any problems, but it's slower than a pure nx session. Is there a way to get NX to show it correctly?

I'm guessing it's something to do with how nxserver checks for changes to the windows, similar to how vnc uses the mirror driver on windows. Anyone know how to get the programs to display properly?

Thanks for your help

---

### Post by daflame on 2008-02-12
> **karatefish said:**
> Hi all,

I've installed the NX server free edition on my computer, and it works really well so far. It doesn't seem to do hardware acceleration, so I'm using it to connect to the local X session. After disabling desktop effects, it works fine, except that accelerated programs don't refresh properly.

I can use standard programs ok, but when I start a vmplayer virtual machine with hardware accelerated graphics, the virtual machine window only refreshes if I cover it with another program and then bring it forward again.

I can use x11vnc (or connect to a vnc session with nx), which shows the virtual machine without any problems, but it's slower than a pure nx session. Is there a way to get NX to show it correctly?

I'm guessing it's something to do with how nxserver checks for changes to the windows, similar to how vnc uses the mirror driver on windows. Anyone know how to get the programs to display properly?

Thanks for your help

I have had the same problem without resolution, but maybe the NX online docs can help?

---

