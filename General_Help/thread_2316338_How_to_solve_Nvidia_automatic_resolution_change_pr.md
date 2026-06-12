---
title: "How to solve Nvidia automatic resolution change problem after every reboot."
date: 2016-03-07
forum: General Help
---

### Post by hellomr82k on 2016-03-07
How to solve automatic resolution change after every reboot. Or Resolution lost after every reboot. Or Resolution changes after log in.

[SIZE=5][SIZE=4]Theme :[/SIZE][SIZE=2] After setting proper resolution in the Nvidia settings. [/SIZE][/SIZE][SIZE=2]Resolution changes automatically after every reboot. This happerns due to the automatic settings of the xrandr. 
[/SIZE][SIZE=5][SIZE=2]
[/SIZE][/SIZE][SIZE=4]Reason of Cause : [SIZE=2]No transfer of EDID information from monitor to the cpu. [/SIZE][/SIZE]
[LIST=1]
[*][SIZE=4][SIZE=2]Usage of third-part monitor[/SIZE][/SIZE]
[*]Usage to Vga-Dvi adapter
[/LIST]
&#8203;
&#8203;[SIZE=4]Solution : [SIZE=2]After installation of Nvidia (not sure with AMD but they can try too) drivers.

**Note 1: Keep a live cd of the operating system, in order to restore the settings if something goes wrong. **

[LIST=1]
[*]Download [dconf Editor]("https://apps.ubuntu.com/cat/applications/dconf-tools/") from software center.
[*]Open dconf Editor
[*]Press Ctrl + F and search for xrandr
[*]You will see something like this
[*]Just uncheck the active option [IMG]http://s27.postimg.org/wmliudkbn/Screenshot_from_2016_03_07_19_25_55.png[/IMG]
[*]Remove the old monitors.xml type this command in terminal ```
 rm ~/.config/monitors.xml
```
[*]Open Nvidia settings with root```
sudo nvidia-settings
```
[*]Go to X Server Display Configuration tab
[*]Select proper resolution you want and click apply
[*]Click "Save to X Configuration File
[/LIST]


[B]Note 2 : If you are doing this for the first time at the moment of saving the configuration file their will no location specified, just click save. And go /etc/X11 and look for xorg.conf if you can't see it. Follow the steps again from 3-9 this at the moment of saving locate it to /etc/X11 and save.
[/B][/SIZE][/SIZE]
11. Click "Show Preview" 
12. Scroll down and edit the Section "Screen"
13. Modify the Option ```
 Option "metamodes" "nvidia-auto-select +0+0; 1360x768_60_0 +0+0"
``` to  ```
Option "metamodes" "1360x768_60_0 +0+0" 
```(This is my resolution settings)

**Note 3 : If you are not able to edit the config in the preview, undo the settings in preview and save. Open File manger with root privileges go to /etc/X11 open xorg.conf with Scratch, gedit, leafpad etc and follow the steps from 12 - 13.**
[IMG]http://s10.postimg.org/546a539qh/Nvidia.png[/IMG]

14. Click "Save"
15. Reboot your system
Done, I hope after the reboot you will be free of this error. 

[SIZE=4]More possible solution : 

[SIZE=3]Create a Xorg file[/SIZE][/SIZE]
[LIST=1]
[*] Create a xorg.conf file by ```
 sudo nvidia-xconfig
```
[*] Look for the Section "Device" part in the xorg.conf file And add this line inside the section ```
 Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322"
```
[*] Save and reboot your machine
[/LIST]

[SIZE=4][SIZE=2]&#8203;[/SIZE][/SIZE][SIZE=3]Modifying the monitors.xml[/SIZE]

[LIST=1]
[*][SIZE=3][SIZE=2]Go to [/SIZE][/SIZE][COLOR=#111111][FONT=Consolas]/.config/monitors.xm[/FONT][/COLOR]l
[*]Add the preferred solution you want.
[*]Change primary display to "yes"
[/LIST]

&#8203;[SIZE=3]Moving t[/SIZE][SIZE=3]he monitors.xml file
[/SIZE]
[LIST=1]
[*][SIZE=3][SIZE=2]&#8203;[/SIZE][/SIZE] mv ~/.config/monitors.xml ~/.config/monitors.xml.bak
[*] That monitors.xml overrides xorg.conf every time reboot.
[*] sudo nvidia-settings
[*] then set you want, save the file to /usr/share/X11/xorg.conf.d/xorg.conf
[/LIST]
[SIZE=3]
Load Nvidia Config Only[/SIZE]
[LIST=1]
[*] Add nvidia-settings --load-config-onl to your startup programs, that should apply your settings each time you login. ( I didn't get this solution explain it in the reply)
[/LIST]

[SIZE=3]Editing the Lightdm.config [SIZE=2]&#8203;
[LIST=1]
[*] Add the following line to /etc/lightdm/lightdm.conf ```
 session-setup-script=<location of the script you saved with arandr>
```
[/LIST]
[SIZE=4]Important Links
[/SIZE][/SIZE][/SIZE] [nvidia-settings - configure the NVIDIA graphics driver]("http://manpages.ubuntu.com/manpages/quantal/en/man1/alt-nvidia-current-settings.1.html")
[SIZE=3][SIZE=2][SIZE=4][[SIZE=2]Display Manger[/SIZE]]("https://wiki.ubuntuusers.de/Displaymanager/")

P.S : [SIZE=2]I was facing this issue from a long time reading different threads and no possible solution, but suddenly got a solution. Thought to share it with others, added all the possible solution I tired. I hope this will solve the resolution error. If you guys have more possible solution reply I will add it. I'm new to forums don't what category will be perfect, Admins move it under a proper categories instead of removing it. I tried to write everything in simple and step wise manner. Ignore grammar xD[/SIZE]
[/SIZE]
[/SIZE][/SIZE]

---

### Post by v3.xx on 2016-03-07
I'm not having a problem with xrandr; just wanted to say nice post :)

---

