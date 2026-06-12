---
title: "Running windows partion in VMPlayer"
date: 2007-02-08
forum: General Help
---

### Post by andrewww on 2007-02-08
So recently, a friend of mine showed me a link to an digg article that explained how to access your windows partition within VMPlayer. ([http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm](http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm))

I thought the idea was great, and i tried to do it myself, but i ran into some problems.  So im here to look for help.

To start off, when I load the .vmx file, VMplayer loads up, and i get this error message.

Cannot open the disk '/home/andrew/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.

Now, i have no idea what is wrong and what to do, since I am a total n00b to ubuntu.  This is as far as i can get.  I just want to know what i can do to make this acutally work, since i did nothing to the file, other than what the tut. said

Thanks for any/all help!


- Andrew

---

### Post by andrewww on 2007-02-08
Also, here is part of the log file where it shows the error

```

Feb 07 20:35:19: vmx| AIOGNRC: Failed to open '/home/andrew/windowsxp.mbr' : Insufficient permissions to access the file (115) (0x3).
Feb 07 20:35:19: vmx| DISKLIB-FLAT  : Opening unbuffered failed; trying Simple
Feb 07 20:35:19: vmx| AIOGNRC: Failed to open '/home/andrew/windowsxp.mbr' : Insufficient permissions to access the file (115) (0x3).
Feb 07 20:35:19: vmx| DISKLIB-FLAT  : "/home/andrew/windowsxp.mbr" : failed to open (38): AIOMgr_Open failed.
Feb 07 20:35:19: vmx| DISKLIB-DSCPTR: Failed to open extents for descriptor file in normal mode
Feb 07 20:35:19: vmx| DISKLIB-LINK  : "/home/andrew/windows.vmdk" : failed to open (Insufficient permission to access file).  
Feb 07 20:35:19: vmx| DISKLIB-CHAIN : "/home/andrew/windows.vmdk" : failed to open (Insufficient permission to access file).
Feb 07 20:35:19: vmx| DISKLIB-LIB   : Failed to open '/home/andrew/windows.vmdk' with flags 0xa (Insufficient permission to access file).
Feb 07 20:35:19: vmx| DISK: Cannot open disk "/home/andrew/windows.vmdk": Insufficient permission to access file (38).
Feb 07 20:35:19: vmx| DISK: Failed to open disk '/home/andrew/windows.vmdk' : Insufficient permission to access file (38) 3023.
Feb 07 20:35:19: vmx| Msg_Post: Error
Feb 07 20:35:19: vmx| [msg.disk.noBackEnd] Cannot open the disk '/home/andrew/windows.vmdk' or one of the snapshot disks it depends on.
Feb 07 20:35:19: vmx| [msg.disk.configureDiskError] Reason: Insufficient permission to access file.----------------------------------------
Feb 07 20:35:25: vmx| Module DiskEarly power on failed.

```

---

### Post by Buelldozer on 2007-02-08
Wow! This is EXACTLY the reason I came here and here's your post not 5 from the top!

I followed the guide at [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html) and it work great with only a couple of problems.

The first one was an issue where my XPSP2 supports NX as does my processor, Feisty however does NOT support the NX flag. You can fix that by following these instructions - [http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1539&sliceId=SAL_Public](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1539&sliceId=SAL_Public)

Now, the other problem is the exact one that you describe. The root cause is that you do not have sufficient permission to open /dev/hda as a "non-root" user and since there is no way to launch vm-player from the menu system with escalated permissions you're kind of stuck.

What you can do, as a workaround, is to open a shell (command line) and type sudo vmplayer. That will launch the VMplayer session with sufficient permissions to open /dev/hda.

That should allow you to launch the player and open your image.

What I would like though is a "fix" where I can launch the player from the menu system instead of a workaround that requires the command line.

Anyone?

---

### Post by andrewww on 2007-02-08
> **Buelldozer said:**
> Wow! This is EXACTLY the reason I came here and here's your post not 5 from the top!

I followed the guide at [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html) and it work great with only a couple of problems.

The first one was an issue where my XPSP2 supports NX as does my processor, Feisty however does NOT support the NX flag. You can fix that by following these instructions - [http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1539&sliceId=SAL_Public](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1539&sliceId=SAL_Public)

Now, the other problem is the exact one that you describe. The root cause is that you do not have sufficient permission to open /dev/hda as a "non-root" user and since there is no way to launch vm-player from the menu system with escalated permissions you're kind of stuck.

What you can do, as a workaround, is to open a shell (command line) and type sudo vmplayer. That will launch the VMplayer session with sufficient permissions to open /dev/hda.

That should allow you to launch the player and open your image.

What I would like though is a "fix" where I can launch the player from the menu system instead of a workaround that requires the command line.

Anyone?


Wow, thanks.  Seemed to work so far :)

---

### Post by Buelldozer on 2007-02-08
I'm glad that got you going!

I'm still hopeful that someone will chime in with a way to launch vmplayer from the menu system with escalated permissions.

---

### Post by dreamwall on 2007-02-10
Does anybody knows why am I getting an "error 21" at GRUB when I run my windows partition through vmplayer?
If I restart my pc and try to boot to windows, it boots just fine...

---

### Post by andrewww on 2007-02-17
Umm, so now whenever i boot into windows, i get an error saying that Windows Must be Activated before i can use it.  Ive done this already in the past, and i do not know why this is coming up.  There is a yes and no box, when i click either or, it closes

---

### Post by troseph on 2007-03-11
I'm getting the same grub error. 
Based off this tutorial: [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

My drive is SATA so I am doing "parted /dev/sda" that being where my windows install is. I get this:
> 
Number  Start       End         Size        Type      File system  Flags
 1      16065s      104856254s  104840190s  extended               lba  
 5      16128s      104856254s  104840127s  logical   ntfs              
 2      104856255s  390716864s  285860610s  primary   ntfs         boot 


&

> Disk /dev/sda: 24321cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 24321,255,63.  Each cylinder is 8225kB.
Partition Table: msdos

Number  Start    End       Size      Type      File system  Flags
 1      1cyl     6526cyl   6526cyl   extended               lba  
 5      1cyl     6526cyl   6525cyl   logical   ntfs              
 2      6527cyl  24320cyl  17794cyl  primary   ntfs         boot 


My .vmdk file looks like this:

> # Disk DescriptorFile

version=1

CID=9428f535

parentCID=ffffffff

createType="fullDevice"



# Extent description

RW 63 FLAT "windowsxp.mbr" 0

RW 390721904 FLAT "/dev/sda" 63



# The Disk Data Base 

#DDB 



ddb.toolsVersion = "6530"

ddb.adapterType = "SATA"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "24321"

I tried changing the line "RW 390721904 FLAT "/dev/sda" 63" to "RW 390721904 FLAT "/dev/sda" 104856255"
But that doesn't work.


My .vmx file is:

> #!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4" 

uuid.location = "56 4d 8c 48 1d e9 53 12-9e 23 96 ef 90 e2 7a 17"
uuid.bios = "56 4d 8c 48 1d e9 53 12-9e 23 96 ef 90 e2 7a 17"

uuid.action = "create" 
checkpoint.vmState = "windows.vmss"

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxppro" 
numvcpus = "1" 
memsize = "392" 
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
ethernet0.generatedAddress = "00:0c:29:e2:7a:17"
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

floppy0.present = "FALSE" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "FALSE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"


---

### Post by Hasen_A on 2007-04-13
I get a BSOD which doesn't stay long enough for me to see the error message nor can I press the pause key. Any suggestions?

Making a shortcut with the following command
```
gksu vmplayer ../windows.vmx
```

---

### Post by SlowAde on 2007-07-18
I experience the same problem error 21 problem with grub.  I followed [these instructions]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html").  I tried to follow them as faithfully as I could but maybe I missed something..

My parted output is as follows :-

Disk /dev/sda: 312499999s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type     File system  Flags
 1      63s         112454s     112392s     primary  fat16             
 2      112455s     305684819s  305572365s  primary  ntfs         boot 
 3      305684820s  312496379s  6811560s    primary  fat32


Disk /dev/sda: 19452cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 19452,255,63.  Each cylinder is 8225kB.
Partition Table: msdos

Number  Start     End       Size      Type     File system  Flags
 1      0cyl      6cyl      6cyl      primary  fat16             
 2      7cyl      19027cyl  19021cyl  primary  ntfs         boot 
 3      19028cyl  19451cyl  424cyl    primary  fat32 

-- snip --


My vmx file is as follows :-

--- snip ---

# Disk DescriptorFile
version=1
CID=9428f535
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "windowsxp.mbr" 0
RW 312499936 FLAT "/dev/sda" 63

# The Disk Data Base
#DDB

ddb.geometry.cylinders = "19452"
ddb.geometry.heads = "255"
ddb.geometry.sectors = "63"
ddb.virtualHWVersion = "4"
ddb.adapterType = "scsi"
ddb.toolsVersion = "0"

floppy0.present = "FALSE"
floppy0.fileName = "/dev/fd0"
floppy0.startConnected = "FALSE"

--- snip ---

It would be great If anyone can spot anything I have got wrong or missed, or is able to suggest something I might try.

Thanks,

Adrian.

> **dreamwall said:**
> Does anybody knows why am I getting an "error 21" at GRUB when I run my windows partition through vmplayer?
If I restart my pc and try to boot to windows, it boots just fine...

---

