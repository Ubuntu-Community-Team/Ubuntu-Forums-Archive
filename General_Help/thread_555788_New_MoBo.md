---
title: "New MoBo"
date: 2007-09-20
forum: General Help
---

### Post by Imsati on 2007-09-20
I just installed a new MoBo and upon booting up Ubuntu for the first time afterwards, my X-server crashed and all I have is a Terminal Prompt. Is there a way to make the MoBo/Video Card/OS talk to each other or should I just do a reinstall?

On a side note, I didn't have to suffer through the pain of a WinXP reactivation after the swap...odd.

--Jay

---

### Post by por100pre1 on 2007-09-20
Try reconfiguring it:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then:

```
startx
```

---

### Post by Imsati on 2007-09-20
Tried both commands and nothing, sadly. Give it a shot with the nv, nvidia, vese, and vga setting but to no avail. No biggie, I'll just reinstall the root stuff later.

---

