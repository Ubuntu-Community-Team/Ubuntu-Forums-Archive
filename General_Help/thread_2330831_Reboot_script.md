---
title: "Reboot script"
date: 2016-07-15
forum: General Help
---

### Post by 4kh3RAm on 2016-07-15
Is reboot all I need in a script to reboot my computer ?

---

### Post by QDR06VV9 on 2016-07-15
I am probably giving you too much Information here... but here is a few with what they do:
To shutdown the system:

```
sudo shutdown -h now 
```

To restart:

```
sudo reboot
```

& one more command for restart:

```
sudo shutdown -r now
```

And if you want to by pass "sudo"
Here is a one liner

```
/usr/bin/dbus-send --system --print-reply --dest="org.freedesktop.ConsoleKit" /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart
```

---

### Post by 4kh3RAm on 2016-07-15
Thanks a lot.

---

### Post by QDR06VV9 on 2016-07-15
Your Very Welcome:)

---

### Post by DuckHook on 2016-07-15
> **runrickus said:**
> ...To shutdown the system:

```
sudo shutdown -h now 
```On some systems, the -h flag will not power the system off. Just bring it to "halt" state. Although it is safe at that point to "pull the plug", this is rather inconvenient. OTOH, the -P switch specifies actual power off. Simpler alternative (but only works for the various 'buntus) is:```
sudo poweroff
```...which is just an alias for```
sudo shutdown -P now
```In the same vein:```
sudo reboot
```...is alias for```
sudo shutdown -r now
```

---

### Post by QDR06VV9 on 2016-07-15
> **DuckHook said:**
> _**On some systems, the -h flag will not power the system off. Just bring it to "halt" state.**_ Although it is safe at that point to "pull the plug", this is rather inconvenient. OTOH, the -P switch specifies actual power off. Simpler alternative (but only works for the various 'buntus) is:```
sudo poweroff
```...which is just an alias for```
sudo shutdown -P now
```In the same vein:```
sudo reboot
```...is alias for```
sudo shutdown -r now
```
Good to know DH...:) thanks! I have not seen that on any of my systems...but will keep it in the old memory jar.:)

---

