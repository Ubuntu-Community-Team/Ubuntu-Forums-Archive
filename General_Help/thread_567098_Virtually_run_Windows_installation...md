---
title: "Virtually run Windows installation.."
date: 2007-10-04
forum: General Help
---

### Post by Naatan on 2007-10-04
Hi,

I have a question that probably isn't that much Ubuntu related, and I probably already know the answer, but im gonna ask it anyway, since Im doing this on Ubuntu and since I want to be a 100% sure.

Is it possible that when I have Ubuntu and Windows installed on the same disk on different partitions, to have my Windows installation run virtually under Ubuntu?

So basically run a windows as a VM but actually use the physically installed version on another partition?

It's hard to put into words, but I hope I make enough sence to get across..

I know you can do this under MacOSX with VMWARE Fusion, but I haven't seen anything like this under Linux/Windows so far..

---

### Post by usif on 2007-10-04
Wonder if this helps....

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

---

### Post by arekmenner on 2007-10-04
I've got a bit of a problem with this method.
When I run parted, I do sudo parted /dev/sda1 (the location of my windows partition)
I get some errors instead of what it's telling me I'll get.

```
GNU Parted 1.7.1
Using /dev/sda1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            
Error: Can't have a partition outside the disk!                           
(parted)
```

---

### Post by zvacet on 2007-10-04
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")

---

### Post by arekmenner on 2007-10-04
That seems like a fine solution, but as far as I can tell it had no support for Windows installations already on the machine.

I already have a virtual installation of Windows that I can use, but VMware fusion uses a Windows installation so well that I had to experiment a bit.

---

### Post by Naatan on 2007-10-04
> **usif said:**
> Wonder if this helps....

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

While going over that walkthrough I run into trouble with the following step:

Type "quit" in parted and make copy of MBR. Copy-paste this command into console:
"dd if=/dev/hda of=windowsxp.mbr bs=512 count=63"

I get the following error:

dd: opening `/dev/hda': No such file or directory

I tried locating hda but cant find it anywhere..

I know this is the first HD but I dont know where its mounted..

anyone?

---

### Post by Naatan on 2007-10-04
Figured it out,

Followed all the steps and now I get the error "File not found: windows.vmdk"

when I browse to the VMDK it gives the warning again, Im absolutely sure the filename and path are correct..

anyone? :(

---

### Post by MrFurious on 2007-10-05
> **arekmenner said:**
> I've got a bit of a problem with this method.
When I run parted, I do sudo parted /dev/sda1 (the location of my windows partition)
I get some errors instead of what it's telling me I'll get.

I ran into the same problem.  In my case, I think it was caused by the inclusion of the partition number.  Try

```
sudo parted /dev/sda
```

maybe?  Hope this helps.

---

### Post by Naatan on 2007-10-05
I indeed have sda as well, 

I looked further and saw that the tutorial on the page thinks everyone uses IDE, well ive got a SATA HD..

Does anyone know how I can configure it to run my windows installation on a SATA HD?

My vmdk looks like so:

```

# Disk DescriptorFile

version=1

CID=9428f535

parentCID=ffffffff

createType="fullDevice"



# Extent description

RW 63 FLAT "windowsxp.mbr" 0

RW 78140096 FLAT "/dev/sda" 63 



# The Disk Data Base 

#DDB 



ddb.toolsVersion = "6530"

ddb.adapterType = "sata"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "4864"

```

and my vmx:

```

config.version = "8"
virtualHW.version = "4"

uuid.location = "56 4d 56 4a 7b d7 4c 30-f5 80 d6 8b c4 59 aa eb" 
uuid.bios = "56 4d 56 4a 7b d7 4c 30-f5 80 d6 8b c4 59 aa eb" 

uuid.action = "create" 
checkpoint.vmState = "" 

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxppro" 
numvcpus = "1" 
memsize = "128" 
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
ethernet0.generatedAddress = "00:0c:29:59:aa:eb" 
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

floppy0.present = "TRUE" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "TRUE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"

extendedConfigFile = "windows.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"
mainmem.UseNamedFile = "FALSE"

```

---

### Post by maybeway36 on 2007-10-05
Man, that's a tricky one. The only program I can think of that does that is Parallels for Mac OS. That's obviously of no help here.

---

### Post by Naatan on 2007-10-05
Actually Vmware Fusion on MAC does it as well

but your right, it doesnt help much ;)

---

### Post by MrFurious on 2007-10-05
> **Naatan said:**
> Does anyone know how I can configure it to run my windows installation on a SATA HD?

In your vmdk, have you tried setting ddb.adapterType to "scsi"?

---

