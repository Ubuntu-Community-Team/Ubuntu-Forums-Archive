---
title: "Patching lirc need help to get the imon pad working."
date: 2008-02-18
forum: General Help
---

### Post by radradrobotanks on 2008-02-18
Hi,

As the title says i'm trying to get the directional pad on the imon remote which comes with the Silverstone lc16m case working. I've tried a few times so far. None of my  attempts have worked. Since I need to apply a patch I havnt been using any of the lirc packages. Heres my current process.

Currently i run mythbuntu.

1. sudo apt-get install build-essentials linux-headers-`uname -r`
My reasoning is that you need your kernels headers and build essentials tools to compile the lirc module against your current kernel.

2. Download lirc-0.8.3pre1-imon-pad2keys.patch and a premade lircd.conf from [http://brakemeier.de/electronics/vdr/lirc-imon.html](http://brakemeier.de/electronics/vdr/lirc-imon.html). Download lirc-0.8.3pre1.tar.bz2 from [http://lirc.sourceforge.net/software/snapshots/](http://lirc.sourceforge.net/software/snapshots/).

3. tar xvjf lirc-0.8.3pre1.tar.bz2
    cd lirc-0.8.3pre1
    patch -p1 < ../lirc-0.8.3pre1-imon-pad2keys.patch
    sudo cp ../lircd.conf /etc/lircd.conf
Extract lirc source. Patch extracted source and copy lircd,conf file into /etc

4. Run "./setup.sh" and select particular driver (usb->imon_pad->Save configuration & run configure)

5. Run "make" compiles selected modules and lirc tools

6. "sudo make install" copies compiled module lirc_imon into kernel and installs lirc tools.

7. "sudo cp contrib/lirc.debian /etc/init.d/lirc"
    "update-rc.d lirc defaults 20" installs init script

8. append "options lirc_imon pad2keys_active=1" to /etc/modules

9. reboot

10. i was hoping every thing would work now but it doesn't. /dev/lirc0 has been created , When i run irw the direction pad only generates "mouse s"

Ive done a whole heap of other odd things just on a whim such as adding a udev rule symlinking /dev/lirc0 to /dev/lirc. Does any1 know what is wrong with my process? Just a few more questions. Im unsure how to get mythtv to listen to the remote? and what does irw do?

---

### Post by nite_man on 2008-03-04
Have the same issue when apply that patch to LIRC 0.8.2. With previous version (0.8.1) that patch worked perfect. Have no idea how to fix that.

---

### Post by lvdk on 2008-03-07
Hi,

Place "options lirc_imon pad2keys_active=1"  in cd /etc/modprobe.d/options and not in /etc/modules 
Use the lirc-0.8.3pre1/remotes/imon/lircd.conf.imon-pad2keys as you lircd.conf file.

Regards,
Luuk

---

