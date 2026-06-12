---
title: "Beryl Not Configuring"
date: 2008-04-29
forum: General Help
---

### Post by Stabilityonitsown on 2008-04-29
hi guys, so I download Beryl-Core-0.2.1 and when I try to configure it I get this
```
checking for BERYL... configure: error: Package requirements (libpng xcomposite >= 0.3 xfixes xdamage xrandr ice sm xinerama libstartup-notification-1.0 >= 0.7) were not met:

No package 'xcomposite' found
No package 'xdamage' found
No package 'libstartup-notification-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BERYL_CFLAGS
and BERYL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by crash91 on 2008-04-29
Why on earth are you installing Beryl?! sudo apt-get fusion-icon 
Also search for "compiz" in add/remove software. Its Beryl's sucessor so i see no reason to continue to use Beryl.

---

### Post by Stabilityonitsown on 2008-04-29
Well I searched compiz in the package manager and well I installed it and restarted GUI then I didn't see it in the menu or anything, I also typed "compiz" in the terminal. so how do I open it lol.

---

### Post by alsamman on 2008-04-29
```
sudo apt-get install fusion-icon
```
this installs the tray icon which you can switch compiz on/off

```
sudo apt-get install compizconfig-settings-manager
```
this is how you install the menu where you can customize the way you want compiz to function

Edit: you can find the compiz manager after installing it in System>Preferences>Advanced Desktop Settings

---

### Post by Stabilityonitsown on 2008-04-29
I'm on Debian >_>. Just forget compiz, just help me get beryl installed, plz.

---

