---
title: "Cannot Open VMWARE Image after Crash"
date: 2007-04-15
forum: General Help
---

### Post by Didjit on 2007-04-15
Argh.

I keep getting this error when trying to open a VMWARE image:

Unable to open: File "/home/chris/Windows XP Professional/Windows XP Professional.vmx" line 1: Syntax error.

System locked at booting the image and rebooted. Now something is out of wack. Any suggestions?

Running Edgy, VMWare Workstation 5.5.3, Image is Windows XP

Please help.....

Didjit

---

### Post by thelinuxguy on 2007-04-15
> **Didjit said:**
> Argh.
I keep getting this error when trying to open a VMWARE image:
Unable to open: File "/home/chris/Windows XP Professional/Windows XP Professional.vmx" line 1: Syntax error.
System locked at booting the image and rebooted. Now something is out of wack. Any suggestions?
Running Edgy, VMWare Workstation 5.5.3, Image is Windows XP
Please help.....
Didjit

Open /home/chris/Windows XP Professional/Windows XP Professional.vmx in a text editor. Check the first few lines and see if anything is missing. My .vmx has these lines. Your file could vary slightly depending on your configuration.

```

#!/opt/vmware/bin/vmware
config.version = "8"
virtualHW.version = "4"
scsi0.present = "TRUE"
memsize = "512"
ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Professional.vmdk"
ide0:0.writeThrough = "TRUE"
ide1:0.present = "TRUE"
ide1:0.fileName = "/media/win_i/Setup/Windows/VS6.iso"
ide1:0.deviceType = "cdrom-image"
floppy0.startConnected = "FALSE"
floppy0.fileName = "/dev/fd0"
Ethernet0.present = "TRUE"
displayName = "XPPro - Virtual"
guestOS = "winxppro"
priority.grabbed = "normal"
priority.ungrabbed = "normal"
powerType.powerOff = "hard"
powerType.powerOn = "hard"
powerType.suspend = "hard"
powerType.reset = "hard"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 36 ee c6 84 6d 7e-3c fc ff 34 65 f9 d5 ed"
uuid.bios = "56 4d 36 ee c6 84 6d 7e-3c fc ff 34 65 f9 d5 ed"
checkpoint.vmState = "Windows XP Professional.vmss"
ethernet0.generatedAddress = "00:0c:29:f9:d5:ed"
ethernet0.generatedAddressOffset = "0"

ide1:0.startConnected = "TRUE"
tools.syncTime = "FALSE"

```

---

### Post by Didjit on 2007-04-15
Thanks for the quick reply. Somehow, my .vmdk and .vmx file were crupted (blank). Thankfully I had a back up.

Things seem to be swell now.

Didjit

---

