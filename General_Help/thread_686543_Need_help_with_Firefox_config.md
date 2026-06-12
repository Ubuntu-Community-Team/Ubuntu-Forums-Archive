---
title: "Need help with Firefox config"
date: 2008-02-03
forum: General Help
---

### Post by txtinman on 2008-02-03
When I go to the edit-preferences-manage area, I do not have a selection for flash file management. I have the flash plugin installed. How do I get the entry I need added?

---

### Post by bwhite82 on 2008-02-03
I am not aware of the flash plugin giving you configuration options (although I could be wrong). What are you trying to accomplish?

---

### Post by txtinman on 2008-02-03
I've visited a few pages that I think need the flash plugin to work. I suspect that the lack of this entry in the configuration panel might be the problem. I thought I could add it with about:config, but I don't know how.

---

### Post by bwhite82 on 2008-02-03
> **txtinman said:**
> I've visited a few pages that I think need the flash plugin to work. I suspect that the lack of this entry in the configuration panel might be the problem. I thought I could add it with about:config, but I don't know how.

To verify that its installed goto: about: plugins

Then test it here:

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

---

### Post by jaytek13 on 2008-02-03
How did you install it? There is currently a bug with installing flash through the browser or using sudo apt-get install flashplugin-nonfree.

If you installed it either of these ways that would explain why it isn't working for you. To get it working you can do it manually:

Go here ( [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux) ) and download the tar.gz package and save it to your desktop

Open a terminal and go to your Desktop directory
```
cd /home/your_username/Desktop
```

Extract the file that you downloaded
```
tar -zxvf install_flash_player_9_linux.tar.gz
```

go into the directory you just extracted
```
cd install_flash_player_9_linux
```

Run the installer
```
sudo ./flashplayer-installer
```


And then restart your browser and flash should be working.

---

### Post by txtinman on 2008-02-03
> **jaytek13 said:**
> How did you install it? There is currently a bug with installing flash through the browser or using sudo apt-get install flashplugin-nonfree.

If you installed it either of these ways that would explain why it isn't working for you. To get it working you can do it manually:

Go here ( [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux) ) and download the tar.gz package and save it to your desktop

Open a terminal and go to your Desktop directory
```
cd /home/your_username/Desktop
```

Extract the file that you downloaded
```
tar -zxvf install_flash_player_9_linux.tar.gz
```

go into the directory you just extracted
```
cd install_flash_player_9_linux
```

Run the installer
```
sudo ./flashplayer-installer
```


And then restart your browser and flash should be working.

That's how I installed it and when I goto about: plugins, it shows to be installed. When I go to the test page, it does not work.

---

