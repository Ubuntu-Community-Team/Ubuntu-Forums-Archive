---
title: "HP Deskjet 694C setup"
date: 2007-02-07
forum: General Help
---

### Post by Stochastic on 2007-02-07
Hi I'm trying to setup my HP Deskjet 694C but I'm having absolutely no luck.  It does autodetect the printer through the installation in my Dapper boot but does not in my Edgy boot.  I have tried many different drivers but none print.  Hp-toolbox does not see/support the printer but according to [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_694C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_694C) everything should work fine.  Does anyone have any advice/pointers/good Howtos/jokes?

---

### Post by Stochastic on 2007-02-09
anyone?

---

### Post by gozzerd on 2007-02-09
can you run 

sudo hp-setup 

?
this sets up a printer for hplip.

---

### Post by Stochastic on 2007-02-09
I don't seem to have that code at my disposal and I don't see any package to install it.

---

### Post by Stochastic on 2007-02-09
here's what the terminal spits out when I run sudo hp-toolbox: ```
sudo hp-toolbox

 HP Linux Imaging and Printing System (ver. 0.9.7)
 HP Device Manager ver. 6.0

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/usr/lib/hplip/ui/devmgr4.py", line 820, in ContinueDeviceListRefresh
    self.UpdateDevice()
  File "/usr/lib/hplip/ui/devmgr4.py", line 721, in UpdateDevice
    self.UpdateTabs()
  File "/usr/lib/hplip/ui/devmgr4.py", line 937, in UpdateTabs
    self.UpdateStatusTab()
  File "/usr/lib/hplip/ui/devmgr4.py", line 1030, in UpdateStatusTab
    if d.tech_type in (TECH_TYPE_COLOR_INK, TECH_TYPE_MONO_INK):
AttributeError: 'Device' object has no attribute 'tech_type'

```

here is hp-probe: ```
sudo hp-probe

 HP Linux Imaging and Printing System (ver. 0.9.7)
 Device Detection (Probe) Utility ver. 1.3

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

   Device URI                                 Model 
   -----------------------------------------  --------------- 
   hp:/par/DESKJET_690C?device=/dev/parport0  HP DESKJET_690C 

```

anyone have any suggestions?  where can I find hp-setup?

---

### Post by Stochastic on 2007-02-09
Hmm, it says here [http://fly.isti.cnr.it/doc/hplip-doc/HTML/install/step4/index.html](http://fly.isti.cnr.it/doc/hplip-doc/HTML/install/step4/index.html) that hp-setup won't work in hplip 0.9.7 or earlier and I'm running version 0.9.7-4ubuntu1.  So I went ahead with the CUPS web interface installation - even though I had attempted to set the printer up before through the gnome printing interface.  But everytime the web interface gets to a user authentication point it won't accept my root password or my current user password or anything else I guess.  Am I supposed to enter something like username: admin password: cups or anything else like that or is there a deeper issue at work here?

---

### Post by Stochastic on 2007-02-09
Okay, even though I feel like I'm talking to myself here, maybe someone will stumble across this issue and lend some advice so here's the latest update on my issue:

Upon further investigation into HPLIP I realized that the version I have 0.9.7 is quite old and they now have 1.7 out.  I have downloaded the source, installed it and ran ```
sudo hp-setup
```.  It looked like everything went as planned (printer was detected, drivers were there, etc..) and it "sent" the test print page.  Nothing printed and the job continued to say "printing" for the next 20min or so.  I cancelled, deleted the printer, re-installed the printer with different drivers - same thing.  In the terminal where I launched hp-setup from (and thus hp-toolbox was auto-launched after setup) I see a repeating error of ```
warning: No status available for device.
``` that reoccurs about every 15seconds.  This is where I sit.  I'm kinda running out of ideas other than buying a new printer or trying windows drivers through wine - though I really doubt that's even possible.  Anyone out there reading this?

---

### Post by gozzerd on 2007-04-06
I would try the install script. I used it on ubuntu edgy. worked great.  It's at hplip.sourceforge.net. It should automatically uninstall old versions, overwrite or re-install the new,  and all the correct dependencies etc. I have a different printer, but I don't think that's the issue.  It's getting the complete hplip system installed.  Once complete, the sudo hp-setup should work. Once correctly installed, the cups controls (localhost:631),  gnome printer administration tool and hp-setup all seem to work fine together.

---

### Post by 11hjpphty76lkjj on 2007-04-09
If the printer is not detected please run:

```
/usr/lib/cups/backend/hp
```

and post the output.

A

---

### Post by 11hjpphty76lkjj on 2007-04-09
> **Stochastic said:**
> Hmm, it says here [http://fly.isti.cnr.it/doc/hplip-doc/HTML/install/step4/index.html](http://fly.isti.cnr.it/doc/hplip-doc/HTML/install/step4/index.html) that hp-setup won't work in hplip 0.9.7 or earlier and I'm running version 0.9.7-4ubuntu1.  So I went ahead with the CUPS web interface installation - even though I had attempted to set the printer up before through the gnome printing interface.  But everytime the web interface gets to a user authentication point it won't accept my root password or my current user password or anything else I guess.  Am I supposed to enter something like username: admin password: cups or anything else like that or is there a deeper issue at work here?

Stochastic:

The documentation there is VERY old, outdated and does us an injustice for the documentation and information we want to provide.  Please only reference or link to:

[http://hplip.sourceforge.net](http://hplip.sourceforge.net)

or any pages under our sourceforge page.

Thanks.

Aaron

---

