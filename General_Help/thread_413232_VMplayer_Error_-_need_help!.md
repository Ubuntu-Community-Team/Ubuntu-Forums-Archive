---
title: "VMplayer Error - need help!"
date: 2007-04-19
forum: General Help
---

### Post by negativesource on 2007-04-19
Hello,

I am a new VMWare user, so this problem may be a very simple one to solve.

I have a dual boot Thinkpad running off a single hard disk.  Both my Ubuntu and Windows partition work properly (I made sure to double-check my windows partition after reviewing this error).  Within Ubuntu, I have successfully installed VMplayer, but when I try to select my Microsoft XP selection at GRUB I get this error:


[IMG]http://negsrc.com/misc/vmplayererror.png[/IMG]

Here is the contents of my .vmdk file that I am using

```

# Disk DescriptorFile
version=1
CID=b57bf7bd
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "windowsxp.mbr" 0
RW 156301424 FLAT "/dev/sda" 63 

# The Disk Data Base 
#DDB

ddb.geometry.cylinders = "9729"
ddb.geometry.heads = "255"
ddb.geometry.sectors = "63"
ddb.virtualHWVersion = "4"
ddb.adapterType = "scsi"
ddb.toolsVersion = "6530"

```

And here is my .vmx file

```

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4" 

uuid.location = <!withheld!> // modification made for forum post
uuid.bios = <!withheld!>  // modification made for forum post
uuid.action = "create" 
checkpoint.vmState = ""

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxppro" 
numvcpus = "1" 
memsize = "2048" 
paevm = "TRUE" 
sched.mem.pshare.enable = "TRUE" 
MemAllowAutoScaleDown = "FALSE" 

MemTrimRate = "-1" 
nvram = "WindowsXP.nvram" 
mks.enable3d = "FALSE" 
vmmouse.present = "FALSE" 
vmmouse.fileName = "auto detect" 

tools.syncTime = "TRUE" 
tools.remindinstall = "FALSE" 
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "TRUE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = <!withheld!>  // modification made for forum post
ethernet0.generatedAddressOffset = "0"

usb.present = "FALSE" 
usb.generic.autoconnect = "FALSE" 

sound.present = "TRUE" 
sound.virtualdev = "sb16" 

ide0:0.present = "TRUE" 
ide0:0.fileName = "windows.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide1:0.present = "TRUE" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom" 
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "TRUE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"

```


I hope that helps, if anyone know what might be the problem I would greatly appreciate it.

THANKS IN ADVANCE

---

### Post by zvacet on 2007-04-19
Like masage sed you didn´t put disc.If you want to have direct access to your windows partition with vmplayer here is 

[http://ubuntuforums.org/showthread.php?t=380699&highlight=native+windows]("http://ubuntuforums.org/showthread.php?t=380699&highlight=native+windows")

Read page two before you do anything.

---

