---
title: "Having problems with graphics drivers on boot (Kubuntu 6.10)"
date: 2006-12-25
forum: General Help
---

### Post by aerojad on 2006-12-25
The first time I booted into Kubuntu, all was fine.  However I needed to install my nvidia drivers, and since then upon reboot the system forgets they're installed, and kdm goes to a blank screen.  Every time I have to stop kdm, reinstall the Nvidia drivers, and then start kdm.  I select the option for the drivers installer to configure the files correctly to automatically load the drivers on startup, and the drivers their selves work just fine, but upon every reboot, it's like I never installed any drivers whatsoever.

---

### Post by aerojad on 2006-12-28
any ideas?  reinstalling drivers every time I boot gets annoying after a bit :/

or is more information required?

---

### Post by mjrclark on 2006-12-29
Longshot here- did you compile your own kernel-module thing to install the drivers, if so are you selecting this set of headers when you boot up in Lilo or Grub, the boot managers?

---

### Post by pgilmon on 2006-12-29
I have installed nvidia drivers. I had to remove a package to get them to work after rebooting. The name of the package is linux-restricted-modules-generic, but if you don't have the default kernel, you have to replace "generic" with your kernel name.

This solution works for me, but it makes my intel wifi stop working. I had to do [this]("http://www.ubuntuforums.org/showpost.php?p=1722490&postcount=2") to get it back to work, but this thing about the wifi only applies to intel 3945ABG wifi, you might have no problem with yours.

I think there might be another solution to the nvidia driver problem that does not require uninstalling any package. Add

```
blacklist nv
```

at the end of the file /etc/modprobe.d/blacklist (create it if it does not exist). I haven't tested this last solution, but you might try. It will prevent "nv" module (free driver for nvidia) from loading, and I think that will allow proprietary module to be loaded. If it doesn't help you can always edit /etc/modprobe.d/blacklist from console and restore it to the previous state. 

Anyway, as I have already said, I haven't tested the second solution, so if you don't feel like experimenting I would recommend you the first one, which worked for me.

---

### Post by aerojad on 2007-01-04
> **pgilmon said:**
> I have installed nvidia drivers. I had to remove a package to get them to work after rebooting. The name of the package is linux-restricted-modules-generic, but if you don't have the default kernel, you have to replace "generic" with your kernel name.

This solution works for me, but it makes my intel wifi stop working. I had to do [this]("http://www.ubuntuforums.org/showpost.php?p=1722490&postcount=2") to get it back to work, but this thing about the wifi only applies to intel 3945ABG wifi, you might have no problem with yours.

I think there might be another solution to the nvidia driver problem that does not require uninstalling any package. Add

```
blacklist nv
```

at the end of the file /etc/modprobe.d/blacklist (create it if it does not exist). I haven't tested this last solution, but you might try. It will prevent "nv" module (free driver for nvidia) from loading, and I think that will allow proprietary module to be loaded. If it doesn't help you can always edit /etc/modprobe.d/blacklist from console and restore it to the previous state. 

Anyway, as I have already said, I haven't tested the second solution, so if you don't feel like experimenting I would recommend you the first one, which worked for me.
I tried both of your solutions, but unfortunately to no avail.  The progress bar when Kubuntu begins to load will go all the way across but right before you expect to see X, the screen flickers, the Kubuntu loading picture shows briefly, and then I am taken back to terminal.

just in case it might be any of the following, here are messages I get while installing the nvidia driver.

> No precompiled kernel interface was found...
And I choose the option to download an interface from Nvidia's site

> No matching precompiled kernel interface was found...
So I hit OK to compile my own

builds the module, finishing installing, asks me if I want the installer to automatically update the config file, I choose yes... and... that's that.  the drivers work, until I reboot once more.

---

### Post by aerojad on 2007-01-06
actually I take that back.  I typed in the wrong kernel modules to remove... apt-get remove linux-restricted-modules-2.6.17-10-generic did the trick.  thank you so much!

---

