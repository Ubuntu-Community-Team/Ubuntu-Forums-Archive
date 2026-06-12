---
title: "Problems with VMware on Ubunutu 7.04 - Won't start again"
date: 2007-07-24
forum: General Help
---

### Post by cognitive on 2007-07-24
Hallo,

I have got a problem with VMware 6.0 on Ubuntu 7.04. When i open the VMX file,
VMware refuses to open it with the following message.

"Unable to open: This virtual machine appears to be in use.
Configutateion file: /home/bs/vmware/WinXP/Windows XP Professional.vmx"

I think the problem comes from an inproper shutdown. So is there a way
to get the machine back working? Otherwise it would be pain in the
*** ...and the last day for VMware.

I hope there is an easy solution.

Best Regards


 

```

######################## Windows XP Professional.vmx ######################## 

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "6"
scsi0.present = "TRUE"
memsize = "1024"
MemAllowAutoScaleDown = "FALSE"
ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Professional.vmdk"
ide1:0.present = "TRUE"
ide1:0.autodetect = "TRUE"
ide1:0.deviceType = "cdrom-raw"
floppy0.startConnected = "FALSE"
floppy0.autodetect = "TRUE"
ethernet0.present = "TRUE"
ethernet0.wakeOnPcktRcv = "FALSE"
usb.present = "TRUE"
ehci.present = "TRUE"
sound.present = "TRUE"
sound.fileName = "-1"
sound.autodetect = "TRUE"
svga.autodetect = "TRUE"
pciBridge0.present = "TRUE"
isolation.tools.hgfs.disable = "FALSE"
displayName = "Windows XP Professional"
guestOS = "winxppro"
nvram = "Windows XP Professional.nvram"
deploymentPlatform = "windows"
virtualHW.productCompatibility = "hosted"
RemoteDisplay.vnc.port = "0"
tools.upgrade.policy = "useGlobal"

floppy0.fileName = "/dev/fd0"

ethernet0.addressType = "generated"
uuid.location = "56 4d fb 78 d1 cd e9 a3-0e 27 88 00 07 b7 0f 3b"
uuid.bios = "56 4d fb 78 d1 cd e9 a3-0e 27 88 00 07 b7 0f 3b"
ide0:0.redo = ""
pciBridge0.pciSlotNumber = "17"
scsi0.pciSlotNumber = "16"
ethernet0.pciSlotNumber = "32"
sound.pciSlotNumber = "33"
ehci.pciSlotNumber = "34"
ethernet0.generatedAddress = "00:0c:29:b7:0f:3b"
ethernet0.generatedAddressOffset = "0"
tools.remindInstall = "FALSE"

ide1:0.startConnected = "FALSE"
ide1:0.fileName = "auto detect"
tools.syncTime = "FALSE"

checkpoint.vmState = ""

usb.autoConnect.device0 = ""

usb.autoConnect.device1 = ""

extendedConfigFile = "Windows XP Professional.vmxf"
sharedFolder.option = "alwaysEnabled"
sharedFolder.maxNum = "1"
sharedFolder0.present = "TRUE"
sharedFolder0.enabled = "TRUE"
sharedFolder0.readAccess = "TRUE"
sharedFolder0.writeAccess = "TRUE"
sharedFolder0.hostPath = "/home/bs/share"
sharedFolder0.guestName = "Linux Share"
sharedFolder0.expiration = "never"

numvcpus = "1"

sound.startConnected = "FALSE"

usb.autoConnect.device2 = ""



######################## Windows XP Professional.vmxf ######################## 


<?xml version="1.0"?>
<Foundry>
<VM>
<VMId type="string">52 b2 f3 ea b0 ea 8d 3a-22 be f1 52 b4 2e 9f 90</VMId>
<ClientMetaData>
<clientMetaDataAttributes/>
<HistoryEventList/></ClientMetaData>
<vmxPathName type="string">Windows XP Professional.vmx</vmxPathName></VM>
<VM>
<VMId type="string">52 37 fd e4 a4 61 28 61-4f f2 9b e5 b8 9b 12 fd</VMId>
<ClientMetaData>
<clientMetaDataAttributes/>
<HistoryEventList/></ClientMetaData>
<vmxPathName type="string">Windows XP Professional.vmx</vmxPathName></VM></Foundry>



```

---

### Post by rasdol on 2007-07-24
did you run it as root?
what vmware do you use: server or workstation?

---

### Post by cognitive on 2007-07-25
Hallo,

Problem is solved. The problem were some folders in the vmware folder. So i deleted
the folders and everything works fine :)


Thx

---

### Post by fabape on 2007-11-05
This is not a Ubuntu issue; it is a VMWare Workstation issue. To fix it, find a file with .lck extension (in the same folder where the .vmx file is) and rename or delete it.

---

