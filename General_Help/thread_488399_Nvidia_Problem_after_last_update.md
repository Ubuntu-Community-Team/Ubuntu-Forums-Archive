---
title: "Nvidia Problem after last update"
date: 2007-06-30
forum: General Help
---

### Post by J.One on 2007-06-30
Hi to all! I run x64version of Feisty and after last update (wich previous all was working fine) now it says that it has a problem in graphical interface and it starts on GRUB.I went on menu.lst from there and i erased the words "splash" and "vga=something" and it's still not working.Any Ideas before i go to format again? And why is this happening?

---

### Post by dexter on 2007-06-30
> **J.One said:**
> Hi to all! I run x64version of Feisty and after last update (wich previous all was working fine) now it says that it has a problem in graphical interface and it starts on GRUB.I went on menu.lst from there and i erased the words "splash" and "vga=something" and it's still not working.Any Ideas before i go to format again? And why is this happening?

What kind of problem is he exactly complaining about ?
Can you still get into a terminal ? If so, try updating your machine:
```

sudo apt-get update
sudo apt-get upgrade

```

You can also try to disable the nvidia driver. You'll have to edit /etc/X11/xorg.conf for that:
sudo pico /etc/X11/xorg.conf go to section "Device" and change nvidia to nv under driver. Save and try starting your graphical display
```

sudo /etc/init.d/gdm restart

```

---

### Post by tpg on 2007-06-30
[This thread]("http://ubuntuforums.org/showthread.php?t=488549") might have the solution you're looking for.

---

