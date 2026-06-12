---
title: "Help to finalize my setup quickcam"
date: 2004-11-13
forum: General Help
---

### Post by Neo40 on 2004-11-13
Hi,

My quickcam is working fine but each time I boot, I need to type this command:

sudo insmod quickcam.ko

Is there a way to load this module automatically? The "quickcam.ko" module is in my home directory. Should I move it to another place?

Thanks for your help.

---

### Post by FLeiXiuS on 2004-11-13
[QUOTE=Neo40]Hi,

My quickcam is working fine but each time I boot, I need to type this command:

sudo insmod quickcam.ko

Is there a way to load this module automatically? The "quickcam.ko" module is in my home directory. Should I move it to another place?

Thanks for your help.[/QUOTE]


Add a line to your /etc/modules.conf.

```
sudo update-modules
```

That will update the modules configurations.  Reboot and give it a shot.

---

