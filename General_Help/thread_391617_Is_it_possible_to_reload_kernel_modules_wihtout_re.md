---
title: "Is it possible to reload kernel modules wihtout rebooting?"
date: 2007-03-23
forum: General Help
---

### Post by B-Con on 2007-03-23
I'm messing around with some madwifi wireless drivers and it's getting kind of annoying rebooting every time I change the kernel modules. Is there a way to load a specific kernel module, or even just reload all of them in a "refresh" sort of way, without rebooting?

---

### Post by Rui Pais on 2007-03-23
hi, to load a module just do:
```
sudo modprobe <modulename>
```

you can hit tab twice after type modprobe to get autocompletion show which modules you have available.

Reboot isnt's necessary.

:)

---

### Post by fanatik on 2007-03-23
In the same way you can use:

```
sudo modprobe -r <module name>
```

to remove a module.

Edit: and use **lsmod** to show all loaded modules.

Cheers,
James.

---

### Post by runemaste644 on 2007-11-17
There is a command to do that. (Although i think it is mainly for a complete kernel upgrade)
It is:
```
kexec
```
I think that ubuntu doesnt support it because when I tried it it said:
```
bash: kexec: Command not found
```
You probably would have to run it as root although.

---

