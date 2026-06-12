---
title: "run seamless rdesktop windows apps at 24bits color!"
date: 2007-03-05
forum: General Help
---

### Post by revertex on 2007-03-05
By default windows XP pro limits the maximum color depth to 16bits for remote desktop, but with a little effort you can change it to 24bits color.

It works pretty fine if you use seamless rdesktop, or any other RDP client inside your lan or locally.

Setup is pretty simple, in windows, go to "start menu">"run" and type gpedit.msc

then go to "administrative templates"> "windows components"> "terminal services" >"limit maximum color depth"

in settings applet, set "enabled" and change color depth from "client compatible" to "24bits".

[[IMG]http://img219.imageshack.us/img219/5272/ts24wy8.th.png[/IMG]]("http://img219.imageshack.us/my.php?image=ts24wy8.png")

You are done, there is no need  to reboot windows.

you also need to change your remote desktop client to connect with 24bits color, in rdesktop use "rdesktop -a 24".

Now you can see some improvement in graphic and multimidia apps compared to default setup.

Cheers.

---

### Post by cowlip on 2007-03-21
Thanks, I didn't know this existed

---

