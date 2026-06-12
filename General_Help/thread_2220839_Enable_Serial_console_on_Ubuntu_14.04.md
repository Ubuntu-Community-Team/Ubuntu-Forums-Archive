---
title: "Enable Serial console on Ubuntu 14.04"
date: 2014-04-29
forum: General Help
---

### Post by Anonymouslemming on 2014-04-29
All,

I'm trying to understand how to setup the serial console on Ubuntu 14.04. I am trying to install this onto a [PC Engines APU]("http://www.pcengines.ch/apu.htm") box and this has no VGA or HDMI out so I need to setup a serial console.

I've looked at links like [http://forums.fedoraforum.org/showthread.php?t=205202](http://forums.fedoraforum.org/showthread.php?t=205202) and [http://www.cyberciti.biz/faq/howto-setup-serial-console-on-debian-linux/](http://www.cyberciti.biz/faq/howto-setup-serial-console-on-debian-linux/) but this doesn't result in a working console - just garbled output. I have ensured that my serial console works with the same speed and parity settings as I'm using to be able to view the apu bios.

The way I am working towards this is by booting the boot device on a box with VGA and working on that. I then move the boot device to the APU and try and boot it there.

Any advice would be much appreciated.

---

### Post by Anonymouslemming on 2014-04-29
> **Anonymouslemming said:**
> All,

I'm trying to understand how to setup the serial console on Ubuntu 14.04. I am trying to install this onto a [PC Engines APU]("http://www.pcengines.ch/apu.htm") box and this has no VGA or HDMI out so I need to setup a serial console.

I've looked at links like [http://forums.fedoraforum.org/showthread.php?t=205202](http://forums.fedoraforum.org/showthread.php?t=205202) and [http://www.cyberciti.biz/faq/howto-setup-serial-console-on-debian-linux/](http://www.cyberciti.biz/faq/howto-setup-serial-console-on-debian-linux/) but this doesn't result in a working console - just garbled output. I have ensured that my serial console works with the same speed and parity settings as I'm using to be able to view the apu bios.

The way I am working towards this is by booting the boot device on a box with VGA and working on that. I then move the boot device to the APU and try and boot it there.

Any advice would be much appreciated.


I've made _some_ progress. I've followed [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto) and after doing that, I can see the boot messages. What I can't see though is a login prompt and cannot login and gain an interactive session.

---

