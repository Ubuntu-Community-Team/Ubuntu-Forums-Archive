---
title: "Kernel 4.2 boot failure in 15.10"
date: 2015-10-23
forum: General Help
---

### Post by alissa-schmidt90 on 2015-10-23
Hello, all.

I upgraded my system from 15.04 to 15.10 yesterday, and now my computer will not boot into the new kernel.  If I boot into kernel 4.2, the computer stalls on the Ubuntu boot screen.  The computer is perfectly happy, however, to boot into kernel 3.16 without any issues.  I can access any logs anyone might need to offer a solution from 3.16 kernel side.  The computer is an AMD processor, HP15; I'm not sure what other details would be helpful, so feel free to ask, and any help you can give me is greatly appreciated.

---

### Post by El Zoido on 2015-10-23
This is just a guess, but have you been using fglrx (the proprietary AMD GPU driver) on 15.04?
There's an unresolved issue with fglrx and the Ubuntu-variant of the 4.2 kernel that causes a kernel panic.

If that's the case:
You can try e.g. booting into the root shell (in the recovery boot menu), then mount the file-system with writing permissions ```
mount -o remount,rw / 
```.
You can now uninstall fglrx through ```
apt-get remove fglrx fglrx-core
```(replace that with fglrx-updates and fglrx-updates-core in case you are using that).
Be careful though, you can potentially do a lot of harm to your system.
Then reboot your system (just type reboot) and if all goes well the system will boot using the free radeon driver.

---

### Post by QIII on 2015-10-23
Sometimes simply removing one will attempt to reinstall the other.  To be sure you get a clean uninstall, you might want to do

```
apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates fglrx-core fglrx-updates-core
```

Using purge rather than remove is often a good idea when uninstalling software because it will get rid of any system configs as well.  Local configs in your /home have to be removed manually.

Your xorg.conf will probably survive the purge, so do

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
```

This will ensure that your system will not try to use the now missing fglrx driver and cause problems.

Please see my very brief discussion at [here]("http://theleftcoastgeek.net/index.php/2-uncategorised/8-fglrx-in-ubuntu-15-10-wily-werewolf-is-a-no-go") for some background on this bug.  There is a link to the bug in Launchpad.  Please click "Affects me too" (or whatever it is) to turn up the flame to get this resolved more quickly.  Also, see Section 3.1 in the ATI wiki link in my signature.

---

