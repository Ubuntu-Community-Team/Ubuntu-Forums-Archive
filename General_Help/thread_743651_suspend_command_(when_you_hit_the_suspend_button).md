---
title: "suspend command (when you hit the suspend button)"
date: 2008-04-02
forum: General Help
---

### Post by mlapaglia on 2008-04-02
i've compiled and installed suspend-0.8 onto ubuntu gutsy, and the command "sudo s2ram --force" successfully makes my computer suspend, and it returns fine as well, sound wireless and all.

right now i have to run this from the command line, how do i make the "suspend" button on the desktop run this command?

thanks

---

### Post by ryanhaigh on 2008-04-10
I don't think you can change this but you could make a launcher and place it on the desktop/panel/menu all you would need to do is change sudo to gksudo to bring up the password dialog and it should work.

---

### Post by gaussian on 2008-04-10
I have done this in the past for hibernate, don't exactly have the details. Basic approach anyway: 
1) You need manually edit scripts in 
```

/usr/lib/hal/scripts/
```
probably 
```

hal-system-power-suspend

```
to get this.
2)  Use dpkg-tools to prevent a future update from overwriting your modifications.

---

