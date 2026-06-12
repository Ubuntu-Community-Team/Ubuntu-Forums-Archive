---
title: "t42, dapper: Problem with initng :-("
date: 2006-07-05
forum: General Help
---

### Post by Mallah on 2006-07-05
Hi ubuntuusers,

first of all my english is not so well,

but i decide to post my problem here, because i hope to get the best support.

after reading the documentation [https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG) about InitNG, i downloaded and compiled the packeges initng version is 0.6.7 an initng-ifiles version is 0.0.5 .

i have a t42 ibm notebook and use dapper. 

i cannot boot with initng. my configs look like these

/boot/grub/menu.lst

> title           Ubuntu, kernel 2.6.15-25-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-25.686 initng
root            (hd0,1)
kernel          /vmlinuz root=/dev/hda2 init=/sbin/initng ro quiet splash
initrd          /initrd.img
savedefault
boot


here are my daemon scripts:
> mallah@mallah-t42:~/Desktop/initng-ifiles-0.0.5/initfiles/daemon$

after reading this :
> If you are installing initng for the first time, you can use gen_system_runlevel to automatically generate the default runlevel based on installed applications.

# gen_system_runlevel -all

Adding services or daemons to your runlevels: 

i use this command to generate the default runlevel.

after all i can find my default.runlevel :
> mallah@mallah-t42:/etc/initng$ ls
default.runlevel  killall5-ignore  system.virtual

default.runlevel looks like this:
> mallah@mallah-t42:/etc/initng$ cat default.runlevel 
system
daemon/acpid
daemon/dbus
daemon/hald
daemon/vixie-cron
deamon/ifplugd
daemon/syslogd
system/alsasound
system/alsasound/cards
system/alsasound/mixerstate
system/laptop-mode
system/speedstep
daemon/klogd
daemon/gdm
daemon/powernowd


and my system.virutual like this...
> mallah@mallah-t42:/etc/initng$ cat system.virtual 
daemon/getty
net/lo
system/clock
system/console-screen
system/hostname
system/modules
system/swap
system/udev
system/urandom
system/usb
system/coldplug



so, and now to my problem: after starting ubuntu with Ubuntu, kernel 2.6.15-25.686 initng i get the failure (message):
> 
FAILSAFE ERROR ** "/home/mallah/Desktop/initng-0.6.7/src/initng_load_module.c", Initng_laoad_module_open() line 196;

00:26:20 Faoö: Symbol "plugin_api_version" not found, the macro INITNG_PLUGIN_MACRO is not added to plugin /lib/initng/libngc2.so::

/lib/initng/libngc2.so: undefined symbol: plugin_api_version

           Next Generation Init Version
                         ......
                         ......
              System is staring up!

** "/home/mallah/Desktop/initng-0.6.7/src/initng_depend.c", initng_depend_start_deps() line;535;

00:26:20 --FAIL: DesktoCould not open `/var/initng_db_backup.v13` for ...

i have no idea, i have done everythink like in the documentation.. but it doesn´t work...

i hope you can help me..

thank you

bye

Mallah

---

### Post by Mallah on 2006-07-08
can nobody help me?

---

