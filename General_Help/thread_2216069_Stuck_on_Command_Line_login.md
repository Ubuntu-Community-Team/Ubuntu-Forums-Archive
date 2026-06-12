---
title: "Stuck on Command Line login"
date: 2014-04-09
forum: General Help
---

### Post by uselessone122 on 2014-04-09
I recently installed kubuntu 13.10 on my computer with an nvidia geforce gts 450 and installed nvidia 334 but the problem with the fonts being too big needed to be fixed so I generated an xorg.conf for nvidia and added the option option "dpi" 96x96 to the monitor section and thats all I added but after rebooting, the computer goes straight to command line login and I dont know what to do now. Any ideas?[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by steeldriver on 2014-04-09
Once you are logged in at the command line, you should be able to get back to the previous state simply by renaming the offending xorg.conf file

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
```

After that, it should be possible to start the GUI using

```
sudo service lightdm start
```

---

