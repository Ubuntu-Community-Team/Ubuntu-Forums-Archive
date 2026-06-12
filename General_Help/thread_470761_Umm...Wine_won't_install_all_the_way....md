---
title: "Umm...Wine won't install all the way..."
date: 2007-06-11
forum: General Help
---

### Post by GeekyWill on 2007-06-11
Well, I went to install Wine today so I could use some apps, and everything went smoothly. However, the installation (in command prompt), stopped when it reached: Setting up wine (0.9.38~winehq0~ubuntu~7.04-1) ... and then it stopped and gave me the command prompt line again! I checked system tools, but it wasn't there, or in anywhere else! Both Add/Remove Application and Synaptic Package Manager said it is installed. Someone help please!

P.S.-I am brand new to Ubuntu, don't assume I know anything advanced unless you tell me how.:(

---

### Post by NikoC on 2007-06-11
Well I forgot which version of wine I had installed, but I had to run it through the terminal as follows:
```
wine windows_app.exe
```

If you already have some apps installed they can be found in your home folder (/home/username) under the hidden .wine directory. In that folder type ```
ls
``` and there should be a folder named c_drive (or something like this) in which a folder /Program Files can be found. There all your via wine installed window apps end up.

You could make shortcuts to the applications by pressing ALT+F2 and enter 'alacarte' without the ' '. This allows you to add new menu entries.

---

### Post by tgm4883 on 2007-06-11
Wine doesn't show up like regular programs.  Go to a command prompt and type winecfg  That will let you configure wine.  Then when you have a exe to run, you either double click on it (if ubuntu is setup to have wine handle exe) or right click and open with wine

---

