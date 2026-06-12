---
title: "Problems with Vmware"
date: 2007-08-05
forum: General Help
---

### Post by Lorek on 2007-08-05
Ok, i'm trying to get my windows xp pro to run in vmplayer on feisty but I keep running into several major hurdles. 

I normally dual boot between ubuntu and WinXP Pro with grub as the bootloader and the mbr being on the windows partition.

I want to setup vmware so I don't need to completely reinstall winxp after i've gone through the whole installation and have all my programs installed already. So i want to set vmware up to access my winxp partition.

Thus far I've got my vm files setup but I keep running into two problems.  The first being the .mbr file i dd'ed turns out to be the grub mbr and not the windows and I can't seem to find where to look for the actual windows bootup mbr. The second problem is when I power the vmachine on and select the windows partition through grub inside vmplayer it crashes right after with this error.

*** VMware Player internal monitor error (bug 9297) ***

The guest operating system you are running is using the Physical Address Extension (PAE) processor option.  For more information about
running PAE-enabled guest operating systems, please consult [http://www.vmware.com/info?id=28](http://www.vmware.com/info?id=28)

I'm pretty sure i've gotten all my config files correct so I really don't know what could be going wrong here.
This is what my config files look like.

WinXP.vmdk
#-----------------------------------
# Disk DescriptorFile
version=1
CID=a108c5db
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "WindowsXP.mbr" 0
RW 488397104 FLAT "/dev/hda" 63

# The Disk Data Base 
#DDB

ddb.toolsVersion = "6530"
ddb.adapterType = "ide"
ddb.virtualHWVersion = "4"
ddb.geometry.sectors = "63"
ddb.geometry.heads = "255"
ddb.geometry.cylinders = "30401"

WinXP.vmx
#-----------------------------------
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"

uuid.location = "56 4d 42 36 9c bc 24 fe-8d 24 bf 98 2a 4c 59 e1"
uuid.bios = "56 4d 42 36 9c bc 24 fe-8d 24 bf 98 2a 4c 59 e1"

uuid.action = "create"
checkpoint.vmState = ""

displayName = "Windows XP Professional"
annotation = ""
guestinfo.vmware.product.long = ""
guestinfo.vmware.product.url = ""

guestOS = "winxppro"
numvcpus = "1"
memsize = "768"
paevm = "FALSE"
sched.mem.pshare.enable = "TRUE"
MemAllowAutoScaleDown = "FALSE"

MemTrimRate = "-1"

nvram = "WindowsXP.nvram"

mks.enable3d = "FALSE"
vmmouse.present = "FALSE"
vmmouse.fileName = "auto detect"

tools.syncTime = "TRUE"
tools.remindinstall = "FALSE"

isolation.tools.hgfs.disable = "TRUE"
isolation.tools.dnd.disable = "FALSE"
isolation.tools.copy.enable = "TRUE"
isolation.tools.paste.enabled = "TRUE"
gui.restricted = "FALSE"

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:4c:59:e1"
ethernet0.generatedAddressOffset = "0"

usb.present = "TRUE"
usb.generic.autoconnect = "TRUE"

sound.present = "TRUE"
sound.virtualdev = "sb16"

ide0:0.present = "TRUE"
ide0:0.fileName = "WindowsXP.vmdk"
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

floppy0.present = "TRUE"
floppy0.fileName = "/dev/fd0"
floppy0.startConnected = "TRUE"

serial0.present = "FALSE"
serial1.present = "FALSE"
parallel0.present = "FALSE"

extendedConfigFile = "WindowsXP.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"
#------------------------------------------------------------------------------------



Besides that I have to run my vmware from the terminal using sudo because for some reason its giving me permission errors when trying to update a snapshot which I have no clue how to fix.

Hopefully someone can help me with this.

---

### Post by leo_m on 2007-09-22
Firstly, it appears that you think that if you capture the windows boot record and refer to it in your vmware settings file, you will be able to boot the windows xp which was intalled outside of the virtual machine on your hard-drive.  Seems like a cool idea in a sense though I do not know if it will be feasible.  Your virtual machine will not be very portable for running Windows even if it were feasible - what do you think?  This is completely alien territory to me and I do not think vmware was designed for such things, though I do know people have found ways to migrate an existing windows installation into a virtual machine (but that process adjusts the installation for hardware changes - you see, virtual machine is different from your real hardware).

Secondly, just to help you a bit, your windows boot record should be on the partition on which you installed windows, not on MBR; e.g., if you installed Windows on /dev/sda1, then doing a ```
dd if=/dev/sda1 of=windows.boot.record bs=1024 count=1
``` should get you  the windows boot record...

Also try googling on ntbackup.exe...

---

