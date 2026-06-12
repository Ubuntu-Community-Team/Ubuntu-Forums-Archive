---
title: "help with virtual machine (windows xp)"
date: 2007-04-23
forum: General Help
---

### Post by zach12 on 2007-04-23
hello
i just installed vmware player and got a virtual machine (windows xp) but when i run the virtual machine i get a error message here it is (Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.)
thank you

---

### Post by beerorkid on 2007-04-23
not sure but you might try a ```
sudo vmware-config.pl 
```

---

### Post by da5id. on 2007-04-23
Hi

I did my Ubuntu with VMware Player, it worked well, not sure if it helps but here is the .vmx file i used, change the path and name to the iso and give it a try..

```
config.version = "8"

virtualHW.version = "4"

displayName = "Ubuntu"

annotation = "Ubuntu 7.04 desktop install"

guestinfo.vmware.product.long = "Ubuntu CD ISO"

guestinfo.vmware.product.url = "http://www.offline.com"

guestinfo.vmware.product.short = "LCDI"

guestinfo.vmware.product.version.major = "1"

guestinfo.vmware.product.version.minor = "0"

guestinfo.vmware.product.version.revision = "0"

guestinfo.vmware.product.version.type = "release"

guestinfo.vmware.product.class = "virtual machine"

guestinfo.vmware.product.build = "1.0.0rc8-20051212"

uuid.action = "create"

guestOS = "winxppro"

#####

# Memory

#####

memsize = "128"

# memsize = "256"

# memsize = "512"

# memsize = "768"

#

# Alternative larger memory allocations

#####

# USB

#####

usb.present = "TRUE"

#####

# Floppy

#####

floppy0.present = "FALSE"

#####

# IDE Storage

#####

ide1:0.present = "TRUE"

#Edit line below to change ISO to boot from

ide1:0.fileName = "iso\ubuntu-7.04-desktop-i386.iso"             <-change this

ide1:0.deviceType = "cdrom-image"

ide1:0.startConnected = "TRUE"

ide1:0.autodetect = "TRUE"

#####

# Network

#####

ethernet0.present = "TRUE"

ethernet0.connectionType = "nat"

ethernet2.present = "TRUE"

ethernet2.connectionType = "nat"

# ethernet0.connectionType = "bridged"

#

# Switch these two to enable "Bridged" vs. "NAT"

#####

# Sound

#####

sound.present = "TRUE"

sound.virtualDev = "es1371"

sound.autoDetect = "TRUE"

sound.fileName = "-1"

#####

# Misc.

#

# (normal)  high

priority.grabbed = "high"

tools.syncTime = "TRUE"

workingDir = "."

#

# (16)  32  64

sched.mem.pShare.checkRate = "32"

#

# (32)  64  128

sched.mem.pshare.scanRate = "64"

#

# Higher resolution lockout, adjust values to exceed 800x600

svga.maxWidth = "1024"

svga.maxHeight = "768"

#

# (F) T

isolation.tools.dnd.disable = "FALSE"

#

# (F) T

isolation.tools.hgfs.disable = "FALSE"

#

# (F) T

isolation.tools.copy.disable = "FALSE"

#

# (F) T

isolation.tools.paste.disable = "FALSE"

#

# (T) F

logging = "TRUE"

#

#

# (F) T

log.append = "FALSE"

#

# (3) number of older files kept

log.keepOld = "1"

#

# (0) microseconds

keyboard.typematicMinDelay = 1000000

uuid.location = "56 4d 8b 6f 33 49 da 71-22 5c 70 dd d8 60 5f c1"

uuid.bios = "56 4d 8b 6f 33 49 da 71-22 5c 70 dd d8 60 5f c1"

ethernet0.addressType = "generated"

ethernet0.generatedAddress = "00:0c:29:60:5f:c1"

ethernet0.generatedAddressOffset = "0"

checkpoint.vmState = "ubuntu-desktop-iso.vmss"



tools.remindInstall = "TRUE"



usb.autoConnect.device0 = "path:1/4/7 autoclean:1"



ethernet1.addressType = "generated"

ethernet2.addressType = "generated"

ethernet1.generatedAddress = "00:0c:29:60:5f:cb"

ethernet1.generatedAddressOffset = "10"

ethernet2.generatedAddress = "00:0c:29:60:5f:d5"

ethernet2.generatedAddressOffset = "20"

```

---

### Post by FluffyElmo on 2007-04-23
Is it possible that you've updated your kernel recently? It may have been in some recent updates. You just have to run the player set-up script again to recompile the kernel module. Note that most of the questions will be already filled in with your current values so you shouldn't have to change anything.

This is something of a pain, and perhaps the restricted module tool will address this at some point but for now you just have to run the script when this happens. Shouldn't happen often...

---

### Post by zach12 on 2007-04-23
my friend is good at linux he have been doing it for a long time 
he had me do the command sudo apt-get install build-essential
to fix it but when do the command i get a error message (E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.)
thank you
ps i am useing a dell inspiron 8000 laptop

---

### Post by zach12 on 2007-04-23
pss i just got buntu and installed vmware a few days ago and got the virtual machine from
this web site [http://www.easyvmx.com/supersimple.shtml](http://www.easyvmx.com/supersimple.shtml)
thank you!:) :) :) :) :)

---

