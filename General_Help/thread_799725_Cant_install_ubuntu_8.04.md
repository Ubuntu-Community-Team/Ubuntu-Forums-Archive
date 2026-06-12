---
title: "Cant install ubuntu 8.04"
date: 2008-05-19
forum: General Help
---

### Post by The Conqueror on 2008-05-19
Ubuntu i386.iso
I installed ubuntu from wubi, and when it asked for reboot it hanged up on the orange progress bar and after a while displayed some errors :

udevd-event [5750] : run_program '/sbin/modprobe' abnormal exit
/etc/rcS.d/s10udev : 105 : usplash_write : not found
init : rcS main process (5455) killed by SEGV Signal
init : Unable to execute "/bin/sh/" for rc-default : No such file or directory
init : rc-default main processs (6687) terminated with status 255

So i uninstalled ubuntu from wubi, and tried to boot from the live cd and i still get the errors :(

my system config is :
c2d e6550
nvidia 8600 GT
1 GB ddr2 RAM
320 GB HDD
samsung 17" LCD monitor

---

### Post by mijanous on 2008-05-19
it seems to me that the cd or cd image was downloaded bad or burned bad or something like this...i had same problem that i got an error then i burned it with new cd and it goes well...but that's only my idea...it could not be your problem....

---

### Post by The Conqueror on 2008-05-19
no i can install ubuntu in vmware successfully so it couldnt be bad cd problem

---

### Post by pixel :-) on 2008-05-21
for problems with wubi post there [http://ubuntuforums.org/forumdisplay.php?f=234]("http://ubuntuforums.org/forumdisplay.php?f=234")

for installation try here [http://ubuntuforums.org/forumdisplay.php?f=333]("http://ubuntuforums.org/forumdisplay.php?f=333")

You have beter chances to get an anser there, here is just the 64 bit version, you have the 32 vertion.Not many peopol will see this post.Move the hole poste there

apparently it failled to load a driver.

Do a "check cd for defects"

boot with faillsafe
boot with out the splash screen and see at what it hangs.Then try to unplug or deactivate whatever is the problem,if it's for example sound, you can survive the install, if it's the hard disk your in trouble.

You can try the alternate install cd.It's a text mode install, more robust to problems.

do you have an usb stick of more then +-700MB?

---

### Post by Sef on 2008-05-21
Moved to Wubi forum.

---

### Post by ago on 2008-05-21
If you have the same problems when you boot from live CD it is not wubi related. It is unlikely that you have a bad ISO since wubi checks the md5. 

The fact that you can install to vm suggest that it might be an incompatibility with your hardware. There are workarounds for that via boot parameters like xforcevesa or acpi=off or irq=poll.

Such workarounds can be enabled from the Live CD (see boot options) or Wubi (press esc at boot). You will have to search for the make and model of your machine to find the appropriate parameters to use.

Also, if you do not find any existing bug in launchpad, open a new one, reporting your hardware issues, so that it can be addressed for good.

---

