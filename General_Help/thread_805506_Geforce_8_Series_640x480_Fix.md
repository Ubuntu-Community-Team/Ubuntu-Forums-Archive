---
title: "Geforce 8 Series 640x480 Fix"
date: 2008-05-24
forum: General Help
---

### Post by mukiex on 2008-05-24
For searchability's sake, I'm stating that this fix is for the following cards :

Geforce 8600 GT GTS
Geforce 8800 GS GT GTS GTX Ultra
Geforce 8500
Geforce 8400

This is for Geforce users suffering from the 640x480 bug, wherein you installed via EnvyNG and got a 640x480 log-on. This *might* fix things for Restricted Driver users as well, but I've only tested it with Envy. If this does not fix things for you, please respond.

Suggested startup procedure :
[LIST]
[*]Go to a terminal: Hold Ctrl+Alt and hit F4
[*]Type in:
```
sudo /etc/init.d/gdm stop
```
[/LIST]

The Fix :
```

cd /etc/X11/
sudo mv xorg.conf xorg.conf.nv640backup
sudo nvidia-xconfig

```

Hit "y", obviously, and let Nvidia fix your xorg.conf. The .nv640backup can be whatever you want, that's just a precautionary measure for anyone whose problem doesn't get fixed by this.

Then :
```

sudo /etc/init.d/gdm start

```
And your display should be fixed!


BONUS! EnvyNG Custom/New Kernel Fix :
Need to reinstall Envy 'cause you just changed kernels? This is the only major tip you need to know:
1. Uninstall the driver from within Envy.
2. RESTART. (Do NOT go to step 3 until you restart, I'm serious. This mistake has driven me insane several times over the years.)
3. Reinstall the driver from within Envy.
4. RESTART.

---

