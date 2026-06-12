---
title: "Golden Cheetah permission error"
date: 2012-11-11
forum: General Help
---

### Post by hollywoodpete on 2012-11-11
Golden Cheetah is a cycling program. I downloaded it from the Software Center after a clean re-install of 12.10 after having a rough time with upgrading from 12.04. I have been unable to down load from my usb cradle after the "upgrade". I keep getting the  "ERROR: open failed: open: Permission denied". I added the powertap.rules file containing SYSFS{idVendor}=="0403", SYSFS{idProduct}=="6001", MODE="666", GROUP="plugdev" but still get the permission error. Has anyone been successful in running 12.10?
If so, is there something else I should do?

---

### Post by hollywoodpete on 2012-11-13
I finally got this to work. Hopefully it will be "plug and play' but mine required a little tweaking. 

1. Remove Britty "sudo apt-get purge Britty"

2. I created a new file as described in the Wiki [https://github.com/srhea/GoldenCheetah/wiki/Powertap-usb-cradle-permissions-on-linux](https://github.com/srhea/GoldenCheetah/wiki/Powertap-usb-cradle-permissions-on-linux)  

"sudo touch /etc/udev/rules.d/powertap.rules"
"sudo gedit /etc/udev/rules.d/powertap.rules"

Cut and paste into the file and save:
"SYSFS{idVendor}=="0403", SYSFS{idProduct}=="6001", MODE="666", GROUP="plugdev"" 

3. This was still not enough to get it to work for me.
I tried " ls -l /dev/ttyUSB0" and got "crw-rw---- 1 root dialout 188, 0 Apr  4 20:49 /dev/ttyUSB0"
" grep dialout /etc/group" resulted in
dialout:x:20:

I realized my username wasn't included in dialout so I added it with:
"sudo usermod -a -G dialout user" with user as my username.

4. Reboot and everything worked fine.

I did recheck " dialout /etc/group" and it resulted in "dialout:x:20:user" with user as my username

I hope this helps.

---

