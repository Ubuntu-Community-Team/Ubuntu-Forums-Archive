---
title: "Help with &quot;Reboot and Select Proper Boot Device&quot; Error Msg"
date: 2014-01-11
forum: General Help
---

### Post by kpkr515 on 2014-01-11
I've only been tinkering with Ubuntu for about a week and these forums have helped me immensely through google search and fixing a lot of other errors I've gotten, but I can't find a solution for this one.

I had a USB bootable flash drive with ubuntu on it and it would start up normally. I tried to create another USB flash drive and that did not work.  I kept making changes in BIOS to get the new one to work and now the original will not boot automatically and I can no longer access BIOS when holding 'F2' at power up with the original USB drive. The original now boots to a screen that allows me to select a couple of options including "Ubuntu" and it boots fine at that point.  So, I'm hoping you guys can get me to the point where I can reaccess BIOS and get the original to boot with no problems and then I would like help getting the new USB stick to boot without the "Reboot and Select Proper Boot Device" Msg.  I've included the Boot-Repair log for the original stick.  

[http://paste.ubuntu.com/6732282/](http://paste.ubuntu.com/6732282/)

Thanks a lot guys.

---

### Post by kpkr515 on 2014-01-11
I fixed the problem with the original USB stick. I'm still having problems with the new one. I had a USB ISP installer using startup disk Kreator. Then I installed to a brand new clean USB stick just like I did the first and I'm getting this error msg.

reboot and select proper boot ddevice 
Or insert boot media in selected boot device and press a kekey 

when I reboot, it will not let me get into bios.
pthanks for your help.

---

### Post by kpkr515 on 2014-01-11
I can get into bios.
boot priority is uefi -> non-ueuefi 

whats wrong?

i have this for advanced-> boboot 
fast mode - enabled
usb - full init
ps2 and mouse- full init

network stack- ddisabled 

next boot after ac loss - fast
launch csm-enabled
boot device control- uefi and legacy
boot from network - legacy oprom
boot from storage -boot from oprom
boot from pcie-boot from oprom
secure boot-ostype - other os

boot option priorities 
1 - uefi sandisk
2 - sandisk

boot override
uefi sandisk
sandisk

---

### Post by kpkr515 on 2014-01-11
I just changed the boot priority from uefi sandisk first to regular sandisk first and i get the same error msg.
Thoughts?

---

