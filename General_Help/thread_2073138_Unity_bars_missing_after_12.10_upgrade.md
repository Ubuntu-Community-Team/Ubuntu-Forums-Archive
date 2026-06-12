---
title: "Unity bars missing after 12.10 upgrade"
date: 2012-10-19
forum: General Help
---

### Post by MountainLion37 on 2012-10-19
Basically, I just upgraded to Quetzal and the resolution and aspect ratio on my display was changed. There is no launcher, no top bar, and the windows (which, by the way, I can only open through the terminal) have no title bars.

---

### Post by Peter09 on 2012-10-19
What graphics card have you got. I have an ATI card and have the same problem. There appears to be an issue with the FGLRX drivers which does not seem to be well publicized. I am not sure where to go with this problem.

---

### Post by timgood on 2012-10-19
> **Peter09 said:**
> What graphics card have you got. I have an ATI card and have the same problem. There appears to be an issue with the FGLRX drivers which does not seem to be well publicized. I am not sure where to go with this problem.

As far as I am aware there is a problem with both NVidia and ATI cards which can be solved by:

```
 sudo apt-get install linux-headers-generic

```

*before* you install the drivers.

Hope this helps.

---

### Post by Mark Phelps on 2012-10-19
Which is why you do NOT upgrade to s new Ubuntu version as soon as it comes out.  I've been upgrading since 7.04, and in EVERY instance, there are problems with the upgrade.

If you check the forums, you'll see that most of us who have gone through this repeatedly advise that folks wait a while AFTER the release to see what problems are reported, before upgrading.

If Canonical ever went to the trouble to provide a "roll back" option (as in, easily rolling back to the previous install), this would not be much of a problem.

---

### Post by timgood on 2012-10-19
> **Mark Phelps said:**
> Which is why you do NOT upgrade to s new Ubuntu version as soon as it comes out.  I've been upgrading since 7.04, and in EVERY instance, there are problems with the upgrade.

If you check the forums, you'll see that most of us who have gone through this repeatedly advise that folks wait a while AFTER the release to see what problems are reported, before upgrading.

If Canonical ever went to the trouble to provide a "roll back" option (as in, easily rolling back to the previous install), this would not be much of a problem.

If no one upgraded, there would be no problems to report. Thus everyone would upgrade thinking there are no problems.

---

### Post by MountainLion37 on 2012-10-19
What should I do now? I installed linux-headers-generic and then nvidia-current-upgrades, and although the screen resolution is back to normal, there still are no bars. I used to use unity --reset to fix this, but the option is deprecated and I have no idea how to fix anything.

---

### Post by Danners on 2012-10-19
Exact same problem here, happened on both my desktop with ATI gfx and my Zenbook Ux31 (Intel hd3000). Disappointing.

---

### Post by jasidog on 2012-10-19
I'm thinking it can't be as common as you'd think as i can't find much about this. 

Yeah anyway, this is really just a me too post. ATI 5870 on a clean 12.10 install. 

Additionaly the reason I want to use the proprietry drivers are that my gpu fan speed seems stuck higher than normal. Plus general performance just seems slow or laggy compared to the 12.04 install this replaced. 

Was hoping the drivers would fix one or both those issues.

Is fine using windows on the same system btw.

---

### Post by MountainLion37 on 2012-10-19
Just for more information, my graphics card is an ATI Radeon HD 3200.

---

### Post by poison-br on 2012-10-19
Well, i had issues today both with my radeon equiped notebook and with my nvidia desktop, ATI seems easier to fix, Nvidia not that easy. Fixed both btw.

For ATI, you need to unistall the FLGRX driver and reboot ( sudo apt-get autoremove fglrx --purge ), for Nvidia install the **NON** proprietary driver, worked here flawless after install and reboot. ( ALt+F2 or CTRL+ALT+T to bring up terminal)
Nvidia: Go to "Software Resources" and click on the "Additional Drivers" tab, select and activate the non proprietary driver and install, reboot. Source: [http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing](http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing) 

Good luck.

> **MountainLion37 said:**
> Basically, I just upgraded to Quetzal and the resolution and aspect ratio on my display was changed. There is no launcher, no top bar, and the windows (which, by the way, I can only open through the terminal) have no title bars.

---

### Post by Peter09 on 2012-10-20
None of this seems to work for me :-(

---

### Post by jasidog on 2012-10-20
> **poison-br said:**
> Well, i had issues today both with my radeon equiped notebook and with my nvidia desktop, ATI seems easier to fix, Nvidia not that easy. Fixed both btw.

For ATI, you need to unistall the FLGRX driver and reboot ( sudo apt-get autoremove fglrx --purge ), for Nvidia install the **NON** proprietary driver, worked here flawless after install and reboot. ( ALt+F2 or CTRL+ALT+T to bring up terminal)
Nvidia: Go to "Software Resources" and click on the "Additional Drivers" tab, select and activate the non proprietary driver and install, reboot. Source: [http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing](http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing) 

Good luck.

Yeah uninstalling the propriety drivers works (ATI) but just leaves us back at square one. Which for me is not a satisfactory square.

---

### Post by bovender on 2012-10-20
Same problem here: Thinkpad T61, Nvidia Quadro NVS140M.

Tried uninstalling (sudo apt-get purge nvidia-current) and re-installing the graphics driver, to no avail.

Will try fresh install of Quantal -- luckily /home is mounted on a separate partition.

---

### Post by bovender on 2012-10-20
Ubuntu 12.10, fresh install now, not Unity regardless of driver (proprietary or nouveau).

I'm going to revert to 12.04 now and wait for 13.04...

---

### Post by RyanRCanada on 2012-10-20
> **poison-br said:**
>  For ATI, you need to unistall the FLGRX driver and reboot ( sudo apt-get autoremove fglrx --purge )

This worked for me, thanks very much!

---

### Post by jajodo on 2012-10-20
Happened to me after installing nvidia drivers.
Found the answer for me here:

[http://ubuntuforums.org/showthread.php?t=2070426](http://ubuntuforums.org/showthread.php?t=2070426)

See reply 7 by KAding

---

### Post by CoreyB. on 2012-10-20
Here is a bug for proprietary drivers not showing up in Additional Drivers (when you know they should be): [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1067104]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1067104")

Make sure to Me Too this bug if you feel it applies to your situation.

---

### Post by jasidog on 2012-10-21
The 2nd part in this post - 

[http://ubuntuforums.org/showpost.php?p=12305917&postcount=11](http://ubuntuforums.org/showpost.php?p=12305917&postcount=11)

worked for me.

As follows - 

> **RedeyeJedi said:**
> This is what worked for me

Removed previous fglrx failed attempt
```
 sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* 
```

Then installing linux-source (not sure if this step is needed but it's what I did)
```
sudo apt-get install linux-source
```

Then install linux-headers-generic
```
sudo apt-get install linux-headers-generic
```

And finally install fglrx-updates
```
sudo apt-get install fglrx-updates
```

And restart
```
sudo reboot
```

I think you can put all the apt-get commands into one but I like to do separately so can keep an eye on em.

I'm not sure which part worked for me. I already had the latest headers installed so it was either "linux-source" or the "fglrx-updates" as previously i'd always tried the simpler sounding "fglrx" package after issues with the updates package in 12.04.

Anyway one or the other worked for me using a ATI 5870 on a clean 12.10 install.

It's solved my jet engined gpu fan sound effects and makes general performance seem more fluid.

---

### Post by Peter09 on 2012-10-21
I got this......

> [Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the AMD driver
 is not installed, the AMD driver is only partially installed,
 or the current AMD driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx-updates_2%3a9.000-0ubuntu3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a9.000-0ubuntu3_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx-updates_2%3a9.000-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by ayyala on 2012-10-25
Ubuntu 12.10 doesn't support AMD/ATI drivers (called fglrx). If you install them, Unity and xserver won't work!

If using AMD/ATI GPU drivers: Run the following command to remove them, and reboot:

```

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

sudo rm /etc/X11/xorg.conf

sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg

sudo reboot

```

Wait for AMD or Canonical or a PPA to release an update that sets the things right.Automated installer and Display Drivers for Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4 are currently supported. 12.10 uses Kernel version 3.5.

Source: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

---

### Post by bovender on 2012-10-27
What finally worked for me was (in addition to installing the linux-headers-generic prior to installing nvidia-current-updates) to (re)move the .config directory in my home directory. Evidently some settings conflicted with the new driver/unity version. With .config moved out of the way, I got unity back.

**Careful:** If you attempt this solution for you, don't *delete* the .config directory as it contains your application settings. For example, I had to execute 'cp .config-old/libreoffice .config' to get my LibreOffice settings back.

---

