---
title: "HPLIP Toolkbox On 12.04"
date: 2013-07-06
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-07-06
Hello,
 
I have 12.10 and have HPLIP Toolbox installed and it will not recognize my printer which is an HP Officejet 4622.  I tried 13.04 and HPLIP Toolbox did recognize my printer.  Is there anyway I can use the HPLIP Toolbox from 13.04 on my 12.10 installation?

Thanks Hannibal

---

### Post by tgalati4 on 2013-07-06
When you open up the hplip application under 12.04 there should be an update button.  Try using that and see if it will update through hplip.  That would be safer than trying a force install of a debian package downloaded from the 13.04 repository.

---

### Post by fantab on 2013-07-07
Are you using 12.04 or 12.10? 
Hplip package from Ubuntu repository for 12.xx will get updates. Is your 12.xx upto date?
Sometimes if the Printer firmware was released after the hplip driver the the support for such printer will be included in the next version of Hplip.

Generally Hplip works quite well, try again. PowerOFF/PowerON, Unplug/replug your printer when you have Ubuntu running. Have you installed hplip-gui? In the installation wizard check if correct ppd file for your printer is selected.

If nothing works then instead of using .deb from 13.04: [try these instructions]("http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html").

---

### Post by coljohnhannibalsmith on 2013-07-14
The last method seems to have worked; thanks all.

Hannibal

---

### Post by coljohnhannibalsmith on 2013-07-30
Hello,

I set up the USB option and everything worked properly; but now, when I tried to set up the wireless option a second HP Logo tries to enter the System Tray and then HPLIP Toolbox reports that there is no System Tray on this device. I also get this error when I click on the HPLIP Toolbox icon without the printer being plugged in.  BTW, I also get 2 HPLIP icons in the System Tray, when I boot up,

Any help appreciated.

Thanks Hannibal

PS., Now,  I can't get HPLIP Toolbox to work at all.

---

### Post by coljohnhannibalsmith on 2013-08-11
Bump!

---

### Post by fantab on 2013-08-11
Try uninstalling the installed HPLIP, and reinstall. But before you uninstall-reinstall try deleting **.hplip** in Home Folder and try to set up the printer again.

Use 'Synaptic Package Manager' to list all the instaled HPLIP packages and libraries. To uninstall completely:

```
sudo dpkg --purge hplip hplip-gui
sudo apt-get remove --purge hplip hplip-gui
sudo apt-get autoremove
```

Dont forget to delete the dot hplip folder located in HOme.

---

### Post by coljohnhannibalsmith on 2013-08-31
Hi,

This didn't work, but I can run my printers.  Also when I try to update to .8 through the Device Manager, this doesn't work either.

Thanks Hannibal

---

### Post by oldfred on 2013-08-31
With my HP Deskjet 3520 I had better luck with the direct download from HP, it was a lot newer version. I do not think I ever ran the tray fix suggestion below, but still had that error, but thought it was because I had 12.04 with gnome-panel and just always ignored the error message.

[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

### Post by ajgreeny on 2013-08-31
> **oldfred said:**
> With my HP Deskjet 3520 I had better luck with the direct download from HP, it was a lot newer version. I do not think I ever ran the tray fix suggestion below, but still had that error, but thought it was because I had 12.04 with gnome-panel and just always ignored the error message.

[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray
+1
I use xubintu 12.04 and had to install hplip direct from their site to get support for one printer, however I have no real knowledge of unity, nor how well hplip  toolbox works in that  but in xubuntu it is great!

---

### Post by coljohnhannibalsmith on 2013-08-31
Hello,

The system tray error fix doesn't work; and I get this message when trying to upgrade from the device manager:

HP Linux Imaging and Printing System (ver. 3.13.7)
HPLIP upgrade latest version ver. 1.0

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Press 'y' to continue to upgrade HPLIP-3.13.8 (y=yes*, n=no):y

Some HPLIP applications are running. Press 'y' to close applications or press 'n' to quit upgrade(y=yes*, n=no):y
error: Failed to close either HP-Toolbox/HP-Systray. Manually close and run hp-upgrade again.
Completed..


Please close this terminal manually.

---

### Post by ajgreeny on 2013-09-01
Try again with the direct downloaded hplip, but this time purge hplip first.

If hplip does not show as installed in software centre or synaptic (my personal favourite package manager), remove it first with the uninstall script in the downloaded archive.

---

