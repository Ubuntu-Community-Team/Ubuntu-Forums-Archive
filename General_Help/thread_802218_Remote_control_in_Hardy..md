---
title: "Remote control in Hardy."
date: 2008-05-21
forum: General Help
---

### Post by kenmiles on 2008-05-21
Can someone please help with a remote problem I am having on Ubuntu 8.04.

I am getting the following output when running this command-
sudo /etc/init.d/lirc restart --verbose
Stopping remote control daemon(s): LIRC                                                                                                                               [fail]
 * Loading LIRC modules                                                                                                                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

The hardware conf is-
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

Thanks in advance for any help, Kenneth.

---

### Post by ToohTaah on 2008-05-23
I too have the same problem since upgrading to Hardy.

Lirc used to work fine in Gutsy.

I have tried to search everywhere, but I have no luck yet. 


```
$ sudo /etc/init.d/lirc restart
[sudo] password for toohtaah:
 * Stopping remote control daemon(s): LIRC                                                               [fail]
 * Loading LIRC modules                                                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

```
$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

```
$ dmesg | grep lirc
[   63.244535] lirc_dev: IR Remote Control driver registered, major 61
[   63.782724] lirc_serial_igor: auto-detected active high receiver
[   63.782729] lirc_dev: lirc_register_plugin: sample_rate: 0
[775690.954966] lirc_dev: IR Remote Control driver registered, major 61
[775690.973468] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[775691.473829] lirc_serial: auto-detected active low receiver
[775691.473834] lirc_dev: lirc_register_plugin: sample_rate: 0

```

Please help me to fix this problem. 

TIA

---

### Post by ebike on 2008-05-31
I have the same issue with a streamzap remote.
My /etc/lirc/hardware.conf is:

> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

I don't know if it helps, when I had lirc_dev in the module list, starting lirc reported failure, I changed that line to just load lirc_streamzap and the error went away. I now get your error when turning on verbose.

Interesting, but the lirc_module is loaded and so is lirc_dev

Trying irw, just produces nothing. I think the developers of Hardy have broken a lot of packages, ALSA doesn't work with several sound cards that used to work great under Gutsy as well, it's a real pain !!

---

### Post by ebike on 2008-05-31
Actually I got mine going, I have had this problem in the past. A new device gets created /dev/lirc1 as well as /dev/lirc0, where /dev/lirc0 used to work, it doesn't now.

As a tempory fix do the following if you have the /dev/lirc1 device.

1. /etc/init.d/lirc stop
2. lircd -d /dev/lirc1
3. Stop and restart the app that is using lirc and you should be good
try with irw

---

### Post by kenmiles on 2008-05-31
Tried that but still the same.
After the last kernel upgrade vmware server will also not work.
Regards, Kenneth.

---

### Post by sandi.newton on 2008-05-31
Hi,
I had the same problem, here's what i did to solve it.

I read somewhere that i had to remove dkms and lirc-modules-source with apt-get --purge and it would work. But it didn't for me.

So i tried "insmod"ing it with insmod lirc_dev and insmod lirc_mceusb. It gave an error that it couldn't find the modules. So i did a locate lirc_dev and did "insmod /lib/modules/2.6.24-17-generic/kernel/drivers/input/misc/lirc_dev.ko" and "insmod /lib/modules/2.6.24-17-generic/kernel/drivers/input/misc/lirc_mceusb2.ko". It went fine, dmesg even showed my remote information.

But when i tried to do /etc/init.d/lirc start it gave the same error of not being able to load. I saw the script, it was trying to load the modules with modprobe -k. I tried to do that manually, i.e modprobe -k lirc_dev , it gave error like "FATAL: Could not open '/lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko': No such file or directory"

So i thought that the script needs dkms to place the modules. So i opened synaptic and installed dkms and lirc-modules-source again. It automatically made the modules and kept it in proper place. I did a locate lirc_dev and it was there in proper place. 

/etc/init.d/lirc start works now. :)

I guess you need to remove dkms and lirc-modules-source and install it again to make it work.

Hope this helps

---

### Post by kenmiles on 2008-05-31
> **sandi.newton said:**
> Hi,
I had the same problem, here's what i did to solve it.

I read somewhere that i had to remove dkms and lirc-modules-source with apt-get --purge and it would work. But it didn't for me.

So i tried "insmod"ing it with insmod lirc_dev and insmod lirc_mceusb. It gave an error that it couldn't find the modules. So i did a locate lirc_dev and did "insmod /lib/modules/2.6.24-17-generic/kernel/drivers/input/misc/lirc_dev.ko" and "insmod /lib/modules/2.6.24-17-generic/kernel/drivers/input/misc/lirc_mceusb2.ko". It went fine, dmesg even showed my remote information.

But when i tried to do /etc/init.d/lirc start it gave the same error of not being able to load. I saw the script, it was trying to load the modules with modprobe -k. I tried to do that manually, i.e modprobe -k lirc_dev , it gave error like "FATAL: Could not open '/lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko': No such file or directory"

So i thought that the script needs dkms to place the modules. So i opened synaptic and installed dkms and lirc-modules-source again. It automatically made the modules and kept it in proper place. I did a locate lirc_dev and it was there in proper place. 

/etc/init.d/lirc start works now. :)

I guess you need to remove dkms and lirc-modules-source and install it again to make it work.

Hope this helps

Tried that and with locate after installing dkms and lirc-modules-source I get -

locate lirc_dev
/lib/modules/2.6.24-16-generic/kernel/drivers/input/misc/lirc_dev.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/ubuntu/media/lirc/lirc_dev/lirc_dev.ko

but still get -

* Stopping remote control daemon(s): LIRC                                                                                                                               [fail]
 * Loading LIRC modules                                                                                                                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

when I restart lirc.

Regards, Kenneth.

---

### Post by sandi.newton on 2008-06-01
> **kenmiles said:**
> Tried that and with locate after installing dkms and lirc-modules-source I get -

locate lirc_dev
/lib/modules/2.6.24-16-generic/kernel/drivers/input/misc/lirc_dev.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/ubuntu/media/lirc/lirc_dev/lirc_dev.ko

but still get -

* Stopping remote control daemon(s): LIRC                                                                                                                               [fail]
 * Loading LIRC modules                                                                                                                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

when I restart lirc.

Regards, Kenneth.

Sorry for late reply,

What does locate lirc_dev give (do an updatedb before you do locate) ??
Mine gives 

/lib/modules/2.6.24-16-generic/kernel/drivers/input/misc/lirc_dev.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/.deps
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/Makefile
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/lirc_dev.c
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/lirc_dev.h
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/.deps/lirc_dev.Po
/var/lib/dkms/lirc/0.8.3~pre1/2.6.24-17-generic/i686/module/lirc_dev.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.deps
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.lirc_dev.ko.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.lirc_dev.mod.o.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.lirc_dev.o.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.tmp_versions
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/Makefile
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/Module.symvers
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.c
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.h
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.mod.c
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.mod.o
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.o
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.deps/lirc_dev.Po
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.tmp_versions/lirc_dev.mod
/var/lib/dkms/lirc/0.8.3~pre1/build/modules/lirc_dev.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/modules/lirc_dev.ko.KVERS
/var/lib/dkms/lirc/original_module/2.6.24-17-generic/i686/lirc_dev.ko


When you installed lirc-modules-source did synaptic did the compile thing required for dkms (You can see it in the details window)? Also dkms needs to be installed first , then lirc_modules_source.

Also, locate your lirc modules and try insmod'ding them . If it works, you can edit /etc/init.d/lirc to do insmod instead of modprobe (function load_module()).

---

### Post by kenmiles on 2008-06-01
Thanks for your reply.

/home/kenneth-->locate lirc_dev
/lib/modules/2.6.24-16-generic/kernel/drivers/input/misc/lirc_dev.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/.deps
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/Makefile
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/lirc_dev.c
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/lirc_dev.h
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/.deps/lirc_dev.Po
/var/lib/dkms/lirc/0.8.3~pre1/2.6.24-17-generic/i686/module/lirc_dev.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.deps
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.lirc_dev.ko.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.lirc_dev.mod.o.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.lirc_dev.o.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.tmp_versions
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/Makefile
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/Module.symvers
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.c
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.h
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.mod.c
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.mod.o
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.o
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.deps/lirc_dev.Po
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.tmp_versions/lirc_dev.mod
/var/lib/dkms/lirc/0.8.3~pre1/build/modules/lirc_dev.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/modules/lirc_dev.ko.KVERS
/var/lib/dkms/lirc/original_module/2.6.24-17-generic/i686/lirc_dev.ko

dkms was installed first and synaptic did the compile as you said.

"Also, locate your lirc modules and try insmod'ding them . If it works, you can edit /etc/init.d/lirc to do insmod instead of modprobe (function load_module())."

I am not sure how to do this.

Regards, Kenneth.

---

### Post by sandi.newton on 2008-06-02
> **kenmiles said:**
> Thanks for your reply.

/home/kenneth-->locate lirc_dev
/lib/modules/2.6.24-16-generic/kernel/drivers/input/misc/lirc_dev.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/ubuntu/media/lirc/lirc_dev
/lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/.deps
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/Makefile
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/lirc_dev.c
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/lirc_dev.h
/usr/src/lirc-0.8.3~pre1/drivers/lirc_dev/.deps/lirc_dev.Po
/var/lib/dkms/lirc/0.8.3~pre1/2.6.24-17-generic/i686/module/lirc_dev.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.deps
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.lirc_dev.ko.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.lirc_dev.mod.o.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.lirc_dev.o.cmd
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.tmp_versions
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/Makefile
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/Module.symvers
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.c
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.h
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.mod.c
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.mod.o
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/lirc_dev.o
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.deps/lirc_dev.Po
/var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_dev/.tmp_versions/lirc_dev.mod
/var/lib/dkms/lirc/0.8.3~pre1/build/modules/lirc_dev.ko
/var/lib/dkms/lirc/0.8.3~pre1/build/modules/lirc_dev.ko.KVERS
/var/lib/dkms/lirc/original_module/2.6.24-17-generic/i686/lirc_dev.ko

dkms was installed first and synaptic did the compile as you said.

"Also, locate your lirc modules and try insmod'ding them . If it works, you can edit /etc/init.d/lirc to do insmod instead of modprobe (function load_module())."

I am not sure how to do this.

Regards, Kenneth.

Ok try this,
sudo insmod /lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko
sudo insmod /lib/modules/2.6.24-17-generic/updates/dkms/lirc_i2c.ko

This should happen cleanly. dmesg|grep lirc should have some output.
If it doesn't tell me your 'uname -r'

---

### Post by kenmiles on 2008-06-02
Thanks again, here is the output from those commands.

/home/kenneth-->sudo insmod /lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko
[sudo] password for kenneth:
insmod: error inserting '/lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko': -1 File exists
/home/kenneth-->sudo insmod /lib/modules/2.6.24-17-generic/updates/dkms/lirc_i2c.ko
insmod: error inserting '/lib/modules/2.6.24-17-generic/updates/dkms/lirc_i2c.ko': -1 File exists
/home/kenneth-->
/home/kenneth-->dmesg|grep lirc
[   79.496800] lirc_dev: IR Remote Control driver registered, major 61
[   79.507538] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
/home/kenneth-->uname -r
2.6.24-17-generic

Regards, Kenneth.

---

### Post by sandi.newton on 2008-06-02
> **kenmiles said:**
> Thanks again, here is the output from those commands.

/home/kenneth-->sudo insmod /lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko
[sudo] password for kenneth:
insmod: error inserting '/lib/modules/2.6.24-17-generic/updates/dkms/lirc_dev.ko': -1 File exists
/home/kenneth-->sudo insmod /lib/modules/2.6.24-17-generic/updates/dkms/lirc_i2c.ko
insmod: error inserting '/lib/modules/2.6.24-17-generic/updates/dkms/lirc_i2c.ko': -1 File exists
/home/kenneth-->
/home/kenneth-->dmesg|grep lirc
[   79.496800] lirc_dev: IR Remote Control driver registered, major 61
[   79.507538] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
/home/kenneth-->uname -r
2.6.24-17-generic

Regards, Kenneth.

I did a google and found this 
[http://ivtvdriver.org/pipermail/ivtv-users/2006-November/004820.html](http://ivtvdriver.org/pipermail/ivtv-users/2006-November/004820.html)

Seems this is a known problem and should be fixed with the next update.
The list also gives instructions on how to solve the problem manually. But it requires compiling lirc from source.

If you are comfortable with that, i recommend doing what the list says.

regards
sandi.newton

---

### Post by kenmiles on 2008-06-04
I have just updated to kernel 2.6.24.18 and the same problem is there.

/home/kenneth-->dmesg | tail
[   89.162856] Bluetooth: RFCOMM ver 1.8
[   89.562381] lirc_dev: IR Remote Control driver registered, major 61
[   89.572991] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[   89.677227] bttv: driver version 0.9.17 loaded
[   89.677236] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   89.862070] ivtv:  Start initialization, version 1.1.0
[   89.862147] ivtv:  End initialization
[   91.668608] tda1004x: setting up plls for 48MHz sampling clock
[   91.952313] tda1004x: found firmware revision 20 -- ok
[  101.049360] eth0: no IPv6 routers present

Regards, Kenneth.

---

### Post by sandi.newton on 2008-06-05
A fix related to lirc kernel module has been commited to hardy-proposed. You can test it and see if it works for you. See [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/218955](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/218955) and [http://blog.omma.net/?p=11](http://blog.omma.net/?p=11)

---

### Post by kenmiles on 2008-06-05
Thanks again for your trouble but that fix did not work either.
I am now thinking of buying a wireless remote instead.
Regards, Kenneth.

---

### Post by mastermindg on 2008-06-05
Hi Kenneth,

I recently performed a clean install of Hardy on my laptop.

I had a lot of the same troubles that you are having now. My solution was to do a manual install of lirc-0.8.3. There is a guide [here]("http://ubuntuforums.org/showthread.php?t=814294").

The device file should default to /dev/lirc0.

Use mode2 -d /dev/lirc0 and irw to troubleshoot.

Good luck.

Also, I am using VMWare server (Free) on both my laptop and my desktop on Hardy. You have to use the update116 patch to get it to compile. There are a few other requirements for scripting libraries. 

Let me know if you need any additional help with this and I can dig through my notes.

---

### Post by kenmiles on 2008-06-06
Thanks, I will try that later today.
By the way, the latest version of VMware server has been updated for Hardy and does not need the patch.
Regards, Kenneth.

---

### Post by mastermindg on 2008-06-08
Thanks for the heads up about the patch.

I patched it when I installed it. No troubles, but good to know if I want to install a newer version.

---

### Post by kenmiles on 2008-06-11
Another update for lirc today and STILL it does not work-

 * Stopping remote control mouse daemon: LIRCMD                                                                                                                          [fail]
 * Stopping remote control daemon(s): LIRC                                                                                                                               [fail]
 * Loading LIRC modules                                                                                                                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

Will this ever be fixed.

---

### Post by Keith_Beef on 2008-11-19
Hmmm... I got one of these Streamzap controllers a couple of days ago.

I tried it tonight for the first time.

I didn't see any effect from pressing the buttons on the controller while running RhytmBox, MPlayer or Xine, so thought there was something broken, as per reports in this thread.

```
$ sudo /etc/init.d/lirc restart --verbose
 * Stopping remote control daemon(s): LIRC                        [fail] 
 * Loading LIRC modules                                           [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
```

Not promising...

Yet:
```
$ lsmod | grep lirc
lirc_streamzap         22916  0 
lirc_dev               22216  1 lirc_streamzap
usbcore               175376  8 lirc_streamzap,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
```

And:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_streamzap"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="PC Remote"
REMOTE_VENDOR="Streamzap"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="PC Remote"
RECEIVER_VENDOR="StreamZap"
```

Now, what seems interesting is that there really is something coming in through /dev/lirc0, as we can see by this:
```
$ sudo cat /dev/lirc0
```

When I press a button on the remote controller, unprintable strings, including BELL appear in the terminal:
```
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;LK&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;LP&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Q&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;T&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;JS&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; € €  € €  € €  € €  € €  € €  € €  € €  € €  € €  € €  € €  €  P € €  € €  € €  € €  € €  € €  €€  € €  € €  € €  € €  € €  € 
                                                 ° € €  € €  € €  € €  € €  € €  € €  € €  € €  € €  € Â4 € €  € €  € €€ €  € €  € €  € €  € €  € €  € €  € †ó € €  € €€ €  € €  € €  € €  € €  € €  € €  € €  € €  € Â2 € €  € €  € €  € €  € €  € €  € €  € €  € €  € €  €€  € 
```

The stuff above is what happens when I press the buttons 1 to 9 on the controller.

So maybe the problem is with the applications (Rhythmbox, et al) not looking at /dev/lirc0 for input?

I tried running Audacious... I have no sound at the moment (see other thread for this), but got some degree of control using the Streamzap.

In the preferences for Audacious, I looked in Plugins -> General tab. Here, I enabled the EvDev-Plug and set the device to /dev/lirc0. I had to change the permissions on this device to be readable my myself. Now I have a small amount of control over Audacious, but the program hangs after using the controls about twelve times... and messages flash by in the terminal where I started Audacious:

```
$ audacious 

** (audacious:18441): WARNING **: event-device-plugin: device \x80Pn\u0002 not found in /dev/input , skipping.

amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
^CAudacious has received SIGINT and is shutting down.
amidi-plug(i_backend.c:i_backend_unload:164): unloading backend 'alsa'
amidi-plug(i_backend.c:i_backend_unload:167): backend 'alsa' unloaded
LASTFM: (cleanup) Cleanup finished
```



K.

---

