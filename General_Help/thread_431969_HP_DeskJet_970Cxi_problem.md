---
title: "HP DeskJet 970Cxi problem"
date: 2007-05-03
forum: General Help
---

### Post by rexio8 on 2007-05-03
Hello!

I have a problem with my printer HP DeskJet 970Cxi attached to my router Asus Wl-500G Premium(by usb). Generally the printer works (prints well when it is on etc) but it should turn on automaticly when a printer job comes in but it doesn't. Is there a way to fix it (make the printer turn on by itself)?. I add the printer with the add printer dialog, choose network printer -> hp jetDirect, write my router ip(192.168.1.1), port 9100 and use the driver hpijs. I've tried to install the driver hplip but it doesn't find my printer at all. 
Thank's for any help.
Tom

---

### Post by john.nicholls on 2007-05-04
Run```
 lsmod | grep ppdev
```
If this produces no output, run ```
modprobe ppdev
``` and restart hplip. To make the change permanent, you then need to add ppdev to /etc/modules.

---

### Post by rexio8 on 2007-05-04
The lsmod produces:
rex@devil:~$  lsmod | grep ppdev
ppdev                  10116  0 
parport                36936  3 ppdev,lp,parport_pc
rex@devil:~$ 
So I guess that the module is on. When I do "sudo hp-setup" the wizard shows up and I choose Network/Ethernet/Wireless (direct connection or JetDirect).. click next and a popup shows up "no devices found. Please make sure your printer is properly connected and powered-on". It certainly is because on windows xp everything works well. I've installed hplip according to this site: [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)
Any more ideas?

---

### Post by john.nicholls on 2007-05-05
When I run "sudo hp-setup" it comes up with the heading followed by

"Using device: hp:/par/deskjet_5600?device=/dev/parport0

Setting up device: hp:/par/deskjet_5600?device=/dev/parport0"

(different printer, of course) before giving me the prompts to respond to. Do you get anything like that?

---

### Post by john.nicholls on 2007-05-05
Tom

I,m responding to this because I installed hplip only a few days ago in order to check on the ink levels in the printer. I had a lot of trouble with the installation and have really only got it partially working.

The commands /usr/lib/hplip/info and /usr/lib/hplip/levels both work properly but /usr/lib/hplip/toolbox throws up two windows with the top one saying No Installed HP Devices found, followed by a number of ways to fix the problem. So I have hplip working sufficiently well to solve my problem, but unfortunately not enough for me to offer you any guidance except to try out their suggestions:

Use hp-setup in a shell/terminal
Use the CUPS web interface by opening a browser to [http://localhost:631](http://localhost:631)
Use the printer installation utility that came with your operating system
After setting up the printer press F6 or choose Device | Refresh All

John

---

### Post by rexio8 on 2007-05-05
Here's the output I get when run hp-setup:
rex@devil:/etc/cups$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 1.7.4a)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: No devices found.Please make sure your printer is properly connected and powered-on.
Done.
python: symbol lookup error: /usr/lib/kde3/plugins/styles/highcolor.so: undefined symbol: _ZN6QGDict5clearEv
rex@devil:/etc/cups$ 
I've also tried all of these suggestions but I just can't choose the hplip driver. 
From the gnome printer add utlity I can choose from: hpijs, cdj550, cdj970, Gunterprint CUPS, pcl3 but no hplip for my model. I've tried all of those drives.. None offers "auto turn on"
Anyway thanks for help.
Regards
Tom

---

