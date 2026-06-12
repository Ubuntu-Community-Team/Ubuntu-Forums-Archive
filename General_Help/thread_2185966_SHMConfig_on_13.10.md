---
title: "SHMConfig on 13.10"
date: 2013-11-05
forum: General Help
---

### Post by strofo on 2013-11-05
I'm trying to configure three finger swipe to change workspace. I'm following this [workaround]("http://ubuntuforums.org/showthread.php?t=2117981"). On Ubuntu 13.04 everything works well, but after upgrading to Ubuntu 13.10 "synclient -m 100" command doesn't work.

```
~$ synclient -m 100
synclient: invalid option -- 'm'
Usage: synclient [-h] [-l] [-V] [-?] [var1=value1 [var2=value2] ...]
  -l List current user settings
  -V Print synclient version string and exit
  -? Show this help message
  var=value  Set user parameter 'var' to 'value'.

```

 I think it's related to SHMConfig. I'm trying to start SHMConfig with xorg.conf from link above, from [this]("https://help.ubuntu.com/community/SynapticsTouchpad") and nothing works. How I can start SHMConfig on Ubuntu 13.10?

---

### Post by sdepablos on 2014-04-02
Try to install [this fork]("https://github.com/felipejfc/xserver-xorg-input-synaptics")  of xserver-xorg-input-synaptics with [COLOR=#333333][FONT=Helvetica]SynapticsSHM back in.[/FONT][/COLOR]

---

