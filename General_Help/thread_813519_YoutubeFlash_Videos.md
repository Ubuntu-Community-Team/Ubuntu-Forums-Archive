---
title: "Youtube/Flash Videos"
date: 2008-05-30
forum: General Help
---

### Post by amtur_poet on 2008-05-30
I'm trying to get a flash plugin working in ubuntu, and it's really annoying. I tried installing the adobe flash plugin, but then it said I needed to download the flash player, which is not in .deb format, and the source code installer didn't seem to work, either. I then tried some other flash plugins, but the same error message about upgrading to the flash player appeared. I can't install the flash plugin, either, because my computer is 64-bit. What should I do to get this working?

---

### Post by alsamman on 2008-05-30
When you install flash from the adobe site, extract the folder. Then you will have libflashplayer.so and flash-installer. Click on flash-installer and then click Run in Terminal then you will be able to install it via terminal.

---

### Post by lud666 on 2008-05-30
I did a fresh install of 8.04 on my amd64 PC, and was able to install flash through the included Firefox 3 beta 5 browser.  Point your browser at youtube or something and you will be prompted to install flash through a yellow bar that drops down from the top, all you have to do is follow the prompts.  I'm pretty sure this is new to 8.04, because I've always had issues with flash before. Hope this helps    :)

---

### Post by wolfen69 on 2008-05-30
go to system>admin>software sources and make sure everything is checked off. then:
```
sudo apt-get install flashplugin-nonfree
```

---

