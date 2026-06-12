---
title: "VMWare player installed but doesn't start up"
date: 2007-09-16
forum: General Help
---

### Post by aseem_mal on 2007-09-16
Hi I downloaded the VMWare 2.0 from vmware.com, ran the install, went through the configuration. All went pretty smooth. At the end, I even got a message saying "Installed successfully. Enjoy your vmware player".

Now it doesn't run if I go: Applications > System Tools > VMWare Player.
Actually, I see a "Starting VMWare Player" item in the bottom task bar... See Screenshot. But soon that too disappears.

Please help.

Thanks,
Aseem:confused:

Oh and I am on Feisty Fawn.

---

### Post by spupy on 2007-09-16
Open a terminal and type the command to start vmware player, must be something like
```
vmware
```
or 
```
vmware-player
```
(possibly as super user)
When you run it in a terminal, any error messages should appear in the output. Post them here, they will give us a closer insight on the problem.

---

### Post by aseem_mal on 2007-09-16
Thanks. I did exactly as you said, but got the same results as I stated in my post at the beginning. Here is a log of what i did:

> aseem@aseem-laptop:~$ vmplayer
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

aseem@aseem-laptop:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Player are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

Extracting the sources of the vmblock module.

Building the vmblock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmblock-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/block.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/control.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dbllnklst.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dentry.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/file.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/inode.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/module.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/stubs.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/super.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-config0/vmblock-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/parport1, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport2, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport3, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet0, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet1, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet8, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Starting VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host network detection                                              done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Player 2.0.0 build-45731 for Linux for this running
kernel completed successfully.

You can now run VMware Player by invoking the following command: 
"/usr/bin/vmplayer".

Enjoy,

--the VMware team


Please help. :confused:

---

### Post by spupy on 2007-09-17
> **aseem_mal said:**
> Thanks. I did exactly as you said, but got the same results as I stated in my post at the beginning. 
Running it in the console, won't fix anything, it was just to show us what error are output.

Anyway, do this:
1. Check if vmware services are running (not sure if this is the best way, but it gets the job done). They most probably are:
```
sudo /etc/initl.d/vmware start
```
2. Try to run vmware (better in console again). If it gives the "has not been (correctly) configured" message, use this command:
```
sudo rm /etc/vmware/not_configured
```
3. Now try to run vmplayer again.
4. Tell us what happened.

---

### Post by fisting_mayfield on 2007-09-17
Hi, I found a workaround, 

copy vmware-player-distrib/installer/services.sh from the vmware tar file
rename services.sh to vmware and cp it to /etc/init.d/
Make sure it's executable (sudo chmod 755 /etc/init.d/vmware)

i was stuck with the same problem for ages, but this has just solved it for me

(credit goes to OsuCowboy for the fix)


-Fist

---

### Post by M7DNYTE on 2007-09-22
So, I likewise have been having this issue also, but with a twist.

I am running VMWare Server.  When I try to run vmware from the applications menu, or in terminal, it does not work.  But if I run it in terminal with:

sudo vmware

it works fine, with only one warning (displayed at end of message).  Anyone know what would cause this?
Running Ubuntu Feisty.

Log of running in terminal without sudo:
"
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-44356/pompeii2005/bora/build/release/wgs/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

"
//  End output for "vmware"

//  Begin output for "sudo vmware"
"
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
"

---

