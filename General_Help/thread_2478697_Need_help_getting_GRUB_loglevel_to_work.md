---
title: "Need help getting GRUB loglevel to work"
date: 2022-09-02
forum: General Help
---

### Post by DrRus on 2022-09-02
Ubuntu 22.04

I have a few ACPI error messages popping up during boot, which I would like to ignore.

I tried setting the loglevel in /etc/default/grub as > GRUB_CMDLINE_LINUX="loglevel=3" running grub-update after, but those messages keep showing on boot.

Any suggestions would be greatly appreciated!

---

### Post by tea for one on 2022-09-02
I think that you have put the parameter on the wrong line.
Try this:-
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="#0000FF"]loglevel=3[/COLOR]"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=true
```

Don't forget ```
sudo update-grub
```

---

### Post by DrRus on 2022-09-02
Awesome, that worked as intended, thanks!

---

