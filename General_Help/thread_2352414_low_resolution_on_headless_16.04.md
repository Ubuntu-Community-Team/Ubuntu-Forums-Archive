---
title: "low resolution on headless 16.04"
date: 2017-02-12
forum: General Help
---

### Post by alku1 on 2017-02-12
Im playing around since hours with my grub config but I cant get around my following issue:

My 16.04. server was running okay with the radeon.modeset=0 command (otherwise reboot issue) while having a screen connected to it.
Since I disconnected the screen I only get a much too low 1024x resolution when connecting by VNC. :(
This is my grub cfg. I tried the GRUB_GFXPAYLOAD_LINUX as well as the GRUB_GFXMODE command with various resolutions and bit, but I dont get anything higher than the 1024x. 
Can anyone help to navigate around this issue with VNC?

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=00
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0"
GRUB_CMDLINE_LINUX=""
#GRUB_GFXPAYLOAD_LINUX=1280x1024x16
GRUB_GFXMODE=1280x1024x32
GRUB_GFXPAYLOAD=keep

---

