---
title: "help! vmware physical partition accident screwed over ubuntu"
date: 2007-06-10
forum: General Help
---

### Post by niclane on 2007-06-10
hi there,

i was setting up a vmware windows machine under ubuntu, it wasn't working i was trying a few things out. then i accidently did what all the tutorials say you have to guard against --- or else! --- i royally screwed up and let ubuntu boot into itself. 

i just tried to reboot, x windows failed, i rebooted again and the hard disk checker kicked in but found a ton of problems and seemed to give up.

can anyone give me instructionst o follow regarding how i can fix up this mess?

any help appreciated.

thanks,

Nicholas.

---

### Post by niclane on 2007-06-10
Apologizes for my prior panic stricken post. I've got a few things due really soon so having my computer going down didn't seem like the best thing that could happen to me on a Sunday night. 

hmm actually i still don't have the windows vm working yet. i suspect the problems are all due to the presence of the sata drive on my laptop, and/or the rescue partition from lenovo. i'll list my config file and setup below and if anyone has any thoughts as to why it is failing it would be great to hear from you 

cheers,

Nicholas

######################

> more winXP.vmdk

# Disk DescriptorFile
version=1
CID=c28f7073
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "winxp.mbr" 0
RW 195371504 FLAT "/dev/sda" 63 

# The Disk Data Base 
#DDB

ddb.geometry.biosSectors = "63"
ddb.geometry.biosHeads = "16"
ddb.geometry.biosCylinders = "1024"
ddb.geometry.cylinders = "12161"
ddb.geometry.heads = "255"
ddb.geometry.sectors = "63"
ddb.virtualHWVersion = "4"
ddb.adapterType = "ide"
ddb.toolsVersion = "0"

############### VMX #########################

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4" 

#uuid.location = "56 4d 42 41 89 44 41 e0-49 62 ad 97 e2 96 3c 8b"
#uuid.bios = "56 4d 42 41 89 44 41 e0-49 62 ad 97 e2 96 3c 8b"

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
tools.remindinstall = "TRUE"
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "TRUE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = "00:0c:29:96:3c:8b"
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
ide0:0.writeThrough = "TRUE" 
ide0:0.startConnected = "TRUE" 

#scsi0.present = "FALSE"
#scsi0.present = "TRUE"
#scsi-1.virtualDev = "lsilogic"
#scsi0:0.present = "TRUE"
#scsi0:0.fileName = "windows.vmdk"
#scsi0:0.writeThrough = "TRUE"
#scsi0:0.deviceType = "rawDisk"

floppy0.present = "FALSE" 
#floppy0.fileName = "/dev/fd0" 
#floppy0.startConnected = "TRUE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"

uuid.location = "56 4d 42 41 89 44 41 e0-49 62 ad 97 e2 96 3c 8b"
uuid.bios = "56 4d 42 41 89 44 41 e0-49 62 ad 97 e2 96 3c 8b"

scsi0.present = "FALSE"

############ PARTED #############

Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s
(parted) print                                                            

Disk /dev/sda: 195371567s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      63s         61432559s   61432497s   primary   ntfs         boot 
 2      61432560s   71547839s   10115280s   primary   fat32             
 3      71553510s   71746289s   192780s     primary   ext3              
 4      71746290s   195366464s  123620175s  extended                    
 6      71746416s   191446604s  119700189s  logical   ext3              
 5      191462670s  195366464s  3903795s    logical   linux-swap        

(parted) unit cyl
(parted) print                                                            

Disk /dev/sda: 12161cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 12161,255,63.  Each cylinder is 8225kB.
Partition Table: msdos

Number  Start     End       Size     Type      File system  Flags
 1      0cyl      3823cyl   3823cyl  primary   ntfs         boot 
 2      3824cyl   4453cyl   629cyl   primary   fat32             
 3      4454cyl   4465cyl   12cyl    primary   ext3              
 4      4466cyl   12160cyl  7695cyl  extended                    
 6      4466cyl   11916cyl  7450cyl  logical   ext3              
 5      11918cyl  12160cyl  243cyl   logical   linux-swap        

(parted)     

######### EOM ###########

---

### Post by flat4 on 2007-07-03
once you get your ubuntu back up an running use virtualbox.org  client, I love it and it easier to create.

---

