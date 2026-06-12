---
title: "Does anyone have a better solution then jockey to install ati or nvidia driver?"
date: 2013-03-08
forum: General Help
---

### Post by aviramof on 2013-03-08
Thanks in advance.

---

### Post by mikewhatever on 2013-03-08
No. Jockey is the best there is.

---

### Post by ManamiVixen on 2013-03-08
I know with nvidia, you can install it from terminal with "sudo apt-get install nvidia-current"

---

### Post by mc4man on 2013-03-08
As mentioned in your other thread jockey is no longer used, you'll find it's replacement in software sources > Drivers tab.

Or you can use sudo apt-get to install or synaptic
(for apt-get you can run this command to list available packages
```
ubuntu-drivers list
```

In 12.10 it's quite likely that [linux-headers-generic was not included in your install]("http://ubuntuforums.org/showthread.php?t=2073060&p=12304169&viewfull=1#post12304169") & the absence of the linux-headers-3.X.X-XX-generic package will prevent the kernel module from being built.

So before installing in any of the various ways - 
```
sudo apt-get install linux-headers-generic
```
bug still open in 12.10, fixed in 13.04 & 12.04.x
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)

---

### Post by aviramof on 2013-03-08
Ok I belive I understood now but still if I install jockey and etc it should have an icon somewhere so that I could use it any time I want and not have to reinstall it everytime.

---

### Post by 3rdalbum on 2013-03-09
> **aviramof said:**
> Ok I belive I understood now but still if I install jockey and etc it should have an icon somewhere so that I could use it any time I want and not have to reinstall it everytime.

No. Jockey is now part of the Software Sources program. Go into Ubuntu Software Center, go to the Edit menu and choose Software Sources. The last tab of the window that opens, allows you to install drivers just like Jockey.

There is no icon for it, because it's merely part of another program. You don't have to "reinstall it" at all, it's already a part of the system.

---

### Post by mc4man on 2013-03-09
With some trepidation I'll relay this to you - 

If you wanted an icon (launcher/.desktop) for "Additional Drivers" then you can easily create one, where & how accessed is your choice, I'll give you 3 examples of where to place. The contents are the same wherever you decide to place (if you do

In local applications folder, accessed thru Dash, search add...
```
mkdir -p ~/.local/share/applications && gedit ~/.local/share/applications/additional-drivers.desktop
```
Use code at bottom of post, save

In /usr/share/applications
```
gksudo gedit /usr/share/applications/additional-drivers.desktop
```
Use code at bottom, save
(may need a log out/in before either of the above show in Dash

On the Desktop
```
gedit ~/Desktop/additional-drivers.desktop
```
Use below code, save. Then run below command to make executable
```
chmod u+x ~/Desktop/additional-drivers.desktop
```

Contents of additional-drivers.desktop

```
[Desktop Entry]
Name=Additional Drivers
Comment=Open Additional tab for hardware drivers available for the system
Icon=jockey
Exec=software-properties-gtk --open-tab=4
Terminal=false
Type=Application
Categories=System;Settings;GTK;HardwareSettings;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=jockey
NoDisplay=false
StartupNotify=true
```

---

### Post by bogan on 2013-03-09
Hi!, **mc4man,**

I second your trepidation!

I have 'Additional Drivers' as a  launcher, created by running AD from the Dash and 'locking to launcher' - a lot easier than your method.

The problem is that the result of running it is different from that displayed in Software Sources>Additional drivers'.

The later correctly shows nvidia-current-updates as installed, activated, and in use. It also shows the Nouveau driver as well as four nvidia drivers.

The former incorrectly states 'No Proprietary drivers are in use in this system', does not show the Nouveau driver, and shows the nvidia-current-updates as: 'activated but not currently in use'. Also it does not list the drivers as 'proprietary' as the later does.

I presume this is because the jockey-kde version installed by apt-get is different from the one installed as default with the kernal.

Whether this also applies to your method I do not know.

Chao!, **bogan.**

---

### Post by mc4man on 2013-03-09
> **bogan said:**
> Hi!, **mc4man,**

I second your trepidation!

I have 'Additional Drivers' as a  launcher, created by running AD from the Dash and 'locking to launcher' - a lot easier than your method.

The problem is that the result of running it is different from that displayed in Software Sources>Additional drivers'.

The later correctly shows nvidia-current-updates as installed, activated, and in use. It also shows the Nouveau driver as well as four nvidia drivers.

The former incorrectly states 'No Proprietary drivers are in use in this system', does not show the Nouveau driver, and shows the nvidia-current-updates as: 'activated but not currently in use'. Also it does not list the drivers as 'proprietary' as the later does.

I presume this is because the jockey-kde version installed by apt-get is different from the one installed as default with the kernal.

Whether this also applies to your method I do not know.

Chao!, **bogan.**

By default in an Ubuntu install there is no "Additional Drivers" available from the Dash as there is no .desktop installed
What happens if one install jockey* I don't know as it shouldn't be installed.

So what I described above should work just fine in 12.10+ - see screen

One small advantage of a Add. drivers specific .desktop is that when opened 'software and updates' will show immediately, the user can then wait till it loads 
(typically 7 -30 secs

As is now in  from the Dash or Ubuntu Software Center when opening software-properties-gtk (Software and Updates here on 13.04),  nothing seems to happen till it loads
(a current bug with no apparent resolution
From synaptic  the user knows something is happening because it gives a spinning cursor till loaded

(the trep was based on knowing the Op to some extent

---

### Post by bogan on 2013-03-10
Hi!, **mc4man,**

I presume you must have several additional PPA's activated to get that many different nvidia drivers, yet not to even include nvidia-current or nvidia-current-updates.

Although I am using the Proposed PPA in 12.10, 3.5.0.26-generic#40, I only get those two, the two experimental 304 & 310 drivers and nouveau, in the system Settings>Software Sources>Additional Drivers display.

Even Synaptic only shows, in addition the 173 and -dev drivers.

Additional Drivers was in Dash from the original 12.10 updated from 12.04.1, but not in a clean install.

Chao!, **bogan**.

---

### Post by mc4man on 2013-03-10
> **bogan said:**
> Hi!, **mc4man,**

I presume you must have several additional PPA's activated to get that many different nvidia drivers, yet not to even include nvidia-current or nvidia-current-updates.

Chao!, **bogan**.
No ppa's, this is just how it's currently laid out in 13.04 (uses driver version & some are duped, screen shows in synaptic.

To note: just noticed that if the created Additional Drivers is opened from Dash then nothing shows until window is fully loaded, if run from the .desktop (launcher) directly then the window opens empty & fills in , around 7 sec here

---

### Post by aviramof on 2013-03-14
Ok so Basicly I hope that in Ubuntu 13.04 they would try to make it easier and more obvious to install the nvidia-current or nvidia-current-updates and etc so the user will have less to worry about in the first few seconds of installing the operating system.:)

---

