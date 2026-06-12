---
title: "Linux-image 4.2.0-28/29 black screen with curson blinking on VMware wks 12.1.0"
date: 2016-02-21
forum: General Help
---

### Post by Alex_Pilone on 2016-02-21
I am using Ubuntu 15.10 on VMware Workstation 12.1.0 (under Windows 10 x64) and until Linux-image 4.2.0-24 everything was OK - after upgrading Ubuntu SW to Linux-image 4.2.0-28 or 4.2.0-29 I am not able to start Ubuntu - after Login I see a black screen with cursor blinking, it seems system blocked! (starting with old Linux-image 4.2.0-24 all is again OK) The same Linux-image 4.2.0-28 or 4.2.0-29 is working perfectly with Oracle VM VirtualBox 5.0.14. Do you known this issue? many thanks

---

### Post by Toni_Vesa on 2016-02-24
I had same problem with Ubuntu 15.10 and linux-image-4.2.0-30-generic 4.2.0-30.35 in VMware Fusion 8.1.0. Black screen with cursor blinking. This error message flashes: **Piix4_SMBus: 000:00:07.3: Host SMBus controller bus not enabled!** I tried this with no luck: [http://askubuntu.com/questions/691729/piix4-smbus-0000007-3-host-smbus-controller-bus-not-enabled](http://askubuntu.com/questions/691729/piix4-smbus-0000007-3-host-smbus-controller-bus-not-enabled). I had to revert to previous version.

---

