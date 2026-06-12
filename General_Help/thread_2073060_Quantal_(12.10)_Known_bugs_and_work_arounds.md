---
title: "Quantal (12.10) Known bugs and work arounds"
date: 2012-10-18
forum: General Help
---

### Post by cariboo on 2012-10-18
Please post the bugs you have run into and how you worked around them here.

Do not post your problems, please raise a support thread.

Keep in mind, that Linux is infinitely customizable, you do not have to stick with Unity as a desktop environment if you do not want to.

I'd suggest you check the [Release Notes]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes"), for the version you are using, before posting a bug.

---

### Post by cariboo on 2012-10-18
There is a known bug concerning raid. The alternate iso has been dropped in favour of moving all the functionality to the Live CD. As of the release of QUantal raid installation don't work.

If you need or want to install Quantal on a raid array, use the [Mini/Netinst]("https://help.ubuntu.com/community/Installation/MinimalCD") iso

**Note** [s]The Quantal mini/netinst iso hasn't been added to this page yet, but should be in the next day or two.[/s] It's there now.

---

### Post by mc4man on 2012-10-19
There seems to be an issue on fresh & maybe upgrade installs when installing any of the nvidia-* drivers.(& probably also  fglrx is the same
linux-headers-generic (linux-headers-3.5.0-17-generic) is not default installed & will not be installed when installing the nvidia-* package
(I believe the dep is improperly satisfied by linux-headers which is default installed

This will cause the kernel module not to be built & when rebooting users will not get a fully working Desktop.

So before installing any of the nvidia drivers or fglrx best to - 
```
sudo apt-get install linux-headers-generic
```

Edit:
It's been decided not to adjust the nvidia-* or fglrx packages so people need to do as above or maybe complain on this bug

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)

---

### Post by novafluxx on 2012-10-19
> **mc4man said:**
> There seems to be an issue on **fresh** installs when installing any of the nvidia-* drivers.
linux-headers-generic (linux-headers-3.5.0-17-generic) is not default installed & will not be installed when installing the nvidia-* package
(I believe the dep is improperly satisfied by linux-headers which is default installed

This will cause the kernel module not to be built & when rebooting users will not get a fully working Desktop.

So before installing any of the nvidia drivers best to - 
```
sudo apt-get install linux-headers-generic
```
Couldn't find a current bug on which was surprising, ??,  so filed one
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1068456](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1068456)

I wonder if that's the same reason the fglrx drivers are not working I will have to test that tomorrow. I will add it to this post if it works out.

I got home and ran ```
apt-get install linux-headers-generic
```

After these were installed I went to software sources and activated the fglrx driver.

I restarted the system and now its working!

```

*-display
       description: VGA compatible controller
       product: PITCAIRN PRO [Radeon HD 7800 Series]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:48 memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:f7e40000-f7e5ffff

```

---

### Post by ricardisimo on 2012-10-19
Couldn't log into GNOME session. Fix: logged in via Unity, ran an update (which I doubt had anything to do with it), logged out and tried GNOME again. Voilá.

Now I need to figure out why my 64-bit machine won't even get to the login screen. Yikes!

---

### Post by bogan on 2012-10-19
Hi!, **all**

RE:** Additional Drivers not available in 12.10 install**.

When I finally, managed to get 12.10 to install [ after trashing an external HDD with 300Gig of data - separate story!] the default driver for my nvidia GT520 would not support Unity 3D -"not software rendered"; although it ran perfectly well in 12.04.

Though the Greeter login screen did not have an option to run anything else until I installed 'gnome-session-fallback'.

I then found that 'Additional Drivers" is not included in the 12.10 release. Entering that in the 'Dash' search opened a specific version of the Software Center, and ten minutes later it was installed, but not to be found anywhere: not in 'Dash', not in 'System Settings', not in 'Synaptic' [ after installing that too ] and not in a terminal [ 'jockey' would not run saying 'jockey-common' was needed ].

Eventually, I installed the 'nvidia-current-updates' 304.51 with 'Synaptic Package Manager' and removed and reinstalled 'Additional Drivers". I noticed that the 'info' stated "This includes the KDE interface".

So I tried: ```
gksudo jockey-kde
``` and "Hey Presto" it worked and 'Additional Drivers" ran, telling me that 'nvidia-current-updates' was installed but not running [ which in fact it was, so that bug is still there!"]. 

BTW: Contrary to recent Posts here I did not have to install the Linux headers or build essential , i n order to install the nvidia driver.

Chao!, **boga**n.

---

### Post by pompel9 on 2012-10-19
Additional drivers has been moved to software sources.

Please have a look at this page [http://www.howopensource.com/2012/10/find-additional-drivers-in-ubuntu-12-10/](http://www.howopensource.com/2012/10/find-additional-drivers-in-ubuntu-12-10/)

---

### Post by smapdi on 2012-10-19
> **novafluxx said:**
> I wonder if that's the same reason the fglrx drivers are not working I will have to test that tomorrow. I will add it to this post if it works out.

Sadly I have the kernel headers installed but no joy in getting fglrx installed/working right.

---

### Post by bogan on 2012-10-19
Hi!,** pompel9,**

Thanks for that info, though the output of Additional Drivers started from Software Sources is different to that when run with 'jockey-kde' from a terminal, the later is in the previous format [ as in 12.04 ] and the former is [slightly] more informative in its listing, including the Nouveau driver, and showing the video card version.

However, unlike the former version it, does not show which driver is installed or in use, merely stating: " One proprietary driver is in use", regardless of which is highlighted.

Chao!, **bogan**.

---

### Post by bogan on 2012-10-19
Hi!, All   **RE: Need for Linux-headers to be installed for video driver installation.**

AFAIK: What is needed is not: 'linux-headers- generic' but, as implied in **mc4man**'s text, but not reflected in the Code, is: ```
sudo apt-get install linux-headers- < uname -r > # Substitute output from 'uname -r'
``` ie the specific header for the currently used kernal version.

Chao!, **bogan.**

---

### Post by Artif on 2012-10-20
> **cariboo907 said:**
> 
Keep in mind, that Linux is infinitely customizable, you do not have to  stick with Unity as a desktop environment if you do not want to.

Yeah! It seems Ubuntu Linux is not the very customizable now days. :/

Issue: after upgrade *-desktop packages may attract unwanted packages into your installation.

Example:  Upgrade LUbuntu 12.04 installation to 12.10. Package lubuntu-desktop  depends on NetworkManager. Network Manager was purged and replaced with  Wicd before upgrade. After upgrade you'll have Wicd + NetworkManager  installed again. It is not possible to remove NM ease due to dependency  of lubuntu-desktop on it.

As workaround was used:
```
dpkg --purge --force-depends network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome
```
after upgrade.

This  will bring up update-notifier in system tray with annoying permanent  message, with red problem sign in tray, about how to get back  Netw.Manag. This was treated as:
```
dpkg --purge --force-depends update-notifier
```

Take a note: these workarounds are ugly. They have side effects.

---

### Post by mvidberg on 2012-10-20
It seems there may be an issue with the filesystem randomly going into read-only mode.  See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1063354](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1063354)

I am running AMD 64bit and updated from 12.04 to 12.10 the other day.  I have / and /home partitions set and noticed yesterday that at random times, one or other of the partitions would suddenly go into read-only mode requiring me to reboot.  Today I've booted into the 3.2.0-32 kernel and so far have not gotten the problem (keeping fingers crossed).  

I've also run smart tests and my HD is reporting as healthy on all tests so I don't think it's my drive and this is indeed the bug reported in that launchpad link.  If anybody else is experiencing this as well, please go to the link and click on "This bug affects me" to give this more attention.

---

### Post by mc4man on 2012-10-20
Not really wanting to dirty up this thread but - 
> **bogan said:**
> Hi!, All   **RE: Need for Linux-headers to be installed for video driver installation.**

AFAIK: What is needed is not: 'linux-headers- generic' but, ....
linux-headers-generic is a meta package & will install the proper linux-headers-generic* as a dep.

---

### Post by grahammechanical on 2012-10-20
> Though the Greeter login screen did not have an option to run anything else until I installed 'gnome-session-fallback'.

It will not, will it?

Unity 2D is not available in 12.10 or ever afterwards. So, unlike 12.04 which put us into Unity 2D if Unity 3D could not be run on the open source drivers, we now have a system that gives a 3D experience without Unity 2D.

So, with the 12.10 login screen we only get one option until we install an alternative desktop environment ourselves.

Regards.

---

### Post by Linuxisfast on 2012-10-20
> **mc4man said:**
> There seems to be an issue on fresh & maybe upgrade installs when installing any of the nvidia-* drivers.(& probably also  fglrx is the same
linux-headers-generic (linux-headers-3.5.0-17-generic) is not default installed & will not be installed when installing the nvidia-* package
(I believe the dep is improperly satisfied by linux-headers which is default installed

This will cause the kernel module not to be built & when rebooting users will not get a fully working Desktop.

So before installing any of the nvidia drivers or fglrx best to - 
```
sudo apt-get install linux-headers-generic
```
Couldn't find a current bug on which was surprising, ??,  so filed one
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1068456](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1068456)
and or
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)


This is a common bug affecting both nvidia and ati, one that will move new users of Ubuntu forever away from the distro. Earlier ati catalyst install would give an error with jockey and thankfully that has been fixed but anyone using hardware driver on 12.10 to install video driver would boot into blank desktop hell. Wonder how this passed through QC.

---

### Post by HRH_H_Crab on 2012-10-21
I have a problem related to fglrx but I am not sure if it is the same as this or not. I have linux-headers-generic installed and I am using an ATI Radeon HD 7500 series card.
If I install the catalyst drivers they don't seem to work properly.
I had a situation yesterday (I upgraded from Precise using do-release-upgrade) where lightdm was convinced that everything was fine (it played the login chimes) and my Xorg.0.log looked o.k. ([http://paste.ubuntu.com/1291873/](http://paste.ubuntu.com/1291873/)) but nothing was coming up on screen.

Everything is working o.k. (well as o.k. as can be expected) with open source drivers. It's particularly annoying as I just bought a new monitor before upgrading to Quetzal and was enjoying HD for the first time since buying my computer! I thought, "wow I'll upgrade to Quetzal" - big mistake now stuck back in the world of open source drivers!

Once I got things working, I tried to install the Catalyst drivers from the gui and while they seemed to be working the screen looked a bit fuzzy. This had happened even under Precise until I rebooted, but in this case I was back to a black screen until I reverted to open source ATI drivers.

---

### Post by GreatDanton on 2012-10-21
One thing I noticed is that, I have 3Ghz processor but I was able to run only on 2Ghz. I solved my problem with program called **cpu frequency scaling indicator**. From now on I am able to reach 3Ghz when I need to (intensive programs etc,..).

Regards.

---

### Post by dino99 on 2012-10-21
> **GreatDanton said:**
> 

your pretzel can only hard landing, but quantal quetzal knows how to fly :P

---

### Post by mabo5184 on 2012-10-21
I also had a problem with the Nvidia driver on my fresh install of ubuntu 12.10.
 
I used the 64bit iso but after trying a few things without success I decided to try the 32bit iso and the Nvidia driver worked fine.

---

### Post by Mark Phelps on 2012-10-23
I installed 12.10 and ran into a problem similar to that in 12.04 -- after a full, successful install, booting would only get a CLI and the (intramfs) prompt.

After some searching, I found and confirmed that the following minor change gets it booting again:

Add "rootdelay=90" to the linux command line parms.

I tried this by first editing boot.cfg -- and it worked great.

Then, I used Grub-customizer to insert this into the default commandline parms, and ran update-grub.

So, if your install appeared to go OK but you now get a text mode screen with (intramfs), try this -- it may work for you.

---

### Post by vivekJohn on 2012-10-24
> **cariboo907 said:**
> Please post the bugs you have run into and how you worked around them here.

Do not post your problems, please raise a support thread.

Keep in mind, that Linux is infinitely customizable, you do not have to stick with Unity as a desktop environment if you do not want to.

I'd suggest you check the [Release Notes]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes"), for the version you are using, before posting a bug.

Thanl You

---

### Post by timgood on 2012-10-25
If you are suffering distorted 'scratchy' sound with Skype 4 you can fix it by: 
```
gksu gedit /etc/pulse/default.pa
```

and changing the line: load-module module-udev-detect
to: load-module module-udev-detect tsched=0

Sound will be OK after reboot.

Hope this helps.

---

### Post by foozball3000 on 2012-10-31
> **Linuxisfast said:**
> This is a common bug affecting both nvidia and ati, one that will move new users of Ubuntu forever away from the distro. Earlier ati catalyst install would give an error with jockey and thankfully that has been fixed but anyone using hardware driver on 12.10 to install video driver would boot into blank desktop hell. Wonder how this passed through QC.

I'm there at the moment. :( Found that I can still use terminal and firefox. So, I'm hoping that installing the linux-headers will get me out of desktop hell.

---

### Post by Linuxisfast on 2012-10-31
> **foozball3000 said:**
> I'm there at the moment. :( Found that I can still use terminal and firefox. So, I'm hoping that installing the linux-headers will get me out of desktop hell.

You have to remove the drivers via sudo apt-get --purge remove and then install the headers and then the drivers.

---

### Post by foozball3000 on 2012-10-31
> **Linuxisfast said:**
> You have to remove the drivers via sudo apt-get --purge remove and then install the headers and then the drivers.

Ah. Thanks. I assume that this is the correct way to remove them then? :
```
sudo apt-get autoremove nvidia-*
sudo apt-get purge nvidia*
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig1
sudo rm /etc/X11/xorg.conf
```

But I might as well install the NVidia closed source drivers, while I'm fixing stuff anyway.

---

### Post by Linuxisfast on 2012-10-31
> **foozball3000 said:**
> Ah. Thanks. I assume that this is the correct way to remove them then? :
```
sudo apt-get autoremove nvidia-*
sudo apt-get purge nvidia*
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig1
sudo rm /etc/X11/xorg.conf
```

But I might as well install the NVidia closed source drivers, while I'm fixing stuff anyway.

Yes and install via hardware drivers and select updates instead of regular as that will keep you up with latest from nvidia and the packaging is not disturbed.

---

### Post by Gray Note on 2012-10-31
Hey guys, I'm new to the forums, this being my first post. Just installed Ubuntu 12.10 six days ago and I encountered a problem with the standby function: even if the screen setting to turn off when inactive is set to 1 hour, my screen turns off every 10 minutes. This is extremely annoying when I am watching videos on Firefox/Chromium. Did this happen to anyone? Is there any way to fix it?

---

### Post by Linuxisfast on 2012-10-31
> **Gray Note said:**
> Hey guys, I'm new to the forums, this being my first post. Just installed Ubuntu 12.10 six days ago and I encountered a problem with the standby function: even if the screen setting to turn off when inactive is set to 1 hour, my screen turns off every 10 minutes. This is extremely annoying when I am watching videos on Firefox/Chromium. Did this happen to anyone? Is there any way to fix it?

In system settings>power management, set the screen off to never.

---

### Post by Gray Note on 2012-10-31
> **Linuxisfast said:**
> In system settings>power management, set the screen off to never.
It was like that before I switched it to 1h and it still turned off, I forgot to mention it in the first post. Still can't figure out why it is happening. Thank you for pointing it out.

---

### Post by Cavsfan on 2012-10-31
> **haqking said:**
> in 12.04 dnsmasq is now running by default due to being hardcoded into network manager.

Potentially bad idea :wink: (ever heard of DNS cache poisoning or MITM attacks ?)

[12.04 Release Notes]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop")

5th Bullet Point.

Its built into Network manager now. 

Running a local DNS caching server where your resolver is localhost or  127.0.01 may speed up DNS resolution but may also pose potential  security risks.

You may do the following to disable it if you dont want it used, though  it doesnt appear it to be caching by default (you can test with the dig  command)


so


```
sudo nano /etc/NetworkManager/NetworkManager.conf
```(the above is case sensitive so capital N)

and comment out the

```
dns=dnsmasq
```line then do a 


```
sudo restart network-manager
```Peace

As **haqking** posted in the bugs/workarounds for 12.04, this apparently still applies to 12.10.
And as **CharlesA** had added: 
Verify /etc/resolv.conf does not say: nameserver 127.0.0.1
```
cat /etc/resolv.conf
```

---

### Post by Cavsfan on 2012-10-31
If any one is interested in getting **Emerald Window Manager** back since it is no longer in the repos, 
the directions on this page worked flawlessly on a few installs.

It works as well on 12.10 as 12.04 too.

[[COLOR=blue]_http://ubuntuportal.com/2012/06/http://www.upubuntu.com/2012/06/how-to-install-emerald-from-source-on.html_[/COLOR]]("http://www.upubuntu.com/2012/06/how-to-install-emerald-from-source-on.html")

But, in the command in CCSM Windows Decoration at the bottom of that page instead of putting just emerald, I put /usr/bin/emerald.

Reboot or logout and it works pretty well. :)

---

### Post by linux4me on 2012-10-31
**Bug: Encrypted External USB Drives Don't Automount**

You can see the thread I started regarding this [here]("http://ubuntuforums.org/showthread.php?p=12328981#post12328981").

The workaround is as follows:

[LIST=1]
[*]Open Disks (Disk Utility in 12.04) by pressing the Super (Windows) key and typing in "Disks." Click the Disks icon.
[*]Locate the encrypted USB drive if it's already plugged in, or plug it in if it's not and it will appear in the left column under Disk Drives.
[*]Click the encrypted drive in Disk Drives to select it.
[*]In the Volumes section, click the padlock icon and enter the passphrase in the dialog that pops up to unlock the drive.
[*]Click the filesystem that appears in Volumes once the drive is unlocked.
[*]Click the icon to mount the file system.
[/LIST]

The drive should now appear in the Launcher and in Nautilus in the Computer section (not in Devices as in 12.04) and you can use it as usual.

---

### Post by buzzmandt on 2012-11-02
The Nvidia bug listed here has affected me for Nvidia 6200 gt.  I could not get this resolved or installed or activated no matter what I tried.  The headers where already installed, but tried reinstalling anyway.  Didn't work.
Currently is running the nouveau driver and it's actually working pretty well.  Otherwise Nvidia is a FAIL.


Other issue for me was broadcomm wireless, actually specifically the NDISWrapper module would not install.  Here is the work around I used very successfully.
1.Download the latest tarball fromhttp://sourceforge.net/projects/ndiswrapper/files/testing/
2. Extract it somewhere then enter that folder in konsole (terminal)
3. run the commands as follows one at a time:
make
sudo make install
modprobe ndiswrapper

this write up can be found here with additional information:
[https://www.facebook.com/notes/kubuntu-ubuntu-kde/ndiswrapper-for-broadcomm-upgrade-from-precise-1204-to-quantal-1210/382409625173154](https://www.facebook.com/notes/kubuntu-ubuntu-kde/ndiswrapper-for-broadcomm-upgrade-from-precise-1204-to-quantal-1210/382409625173154)

---

### Post by Linuxisfast on 2012-11-02
> **buzzmandt said:**
> The Nvidia bug listed here has affected me for Nvidia 6200 gt.  I could not get this resolved or installed or activated no matter what I tried.  The headers where already installed, but tried reinstalling anyway.  Didn't work.
Currently is running the nouveau driver and it's actually working pretty well.  Otherwise Nvidia is a FAIL.


Other issue for me was broadcomm wireless, actually specifically the NDISWrapper module would not install.  Here is the work around I used very successfully.
1.Download the latest tarball fromhttp://sourceforge.net/projects/ndiswrapper/files/testing/
2. Extract it somewhere then enter that folder in konsole (terminal)
3. run the commands as follows one at a time:
make
sudo make install
modprobe ndiswrapper

this write up can be found here with additional information:
[https://www.facebook.com/notes/kubuntu-ubuntu-kde/ndiswrapper-for-broadcomm-upgrade-from-precise-1204-to-quantal-1210/382409625173154](https://www.facebook.com/notes/kubuntu-ubuntu-kde/ndiswrapper-for-broadcomm-upgrade-from-precise-1204-to-quantal-1210/382409625173154)



The newer version of nvidia won't install on your card,add the xswat ppa and install 173 drivers.

---

### Post by Pyloo on 2012-11-04
> **Linuxisfast said:**
> [QUOTE=Gray Note;12328205]Hey guys, I'm new to the forums, this being my  first post. Just installed Ubuntu 12.10 six days ago and I encountered a  problem with the standby function: even if the screen setting to turn  off when inactive is set to 1 hour, my screen turns off every 10  minutes. This is extremely annoying when I am watching videos on  Firefox/Chromium. Did this happen to anyone? Is there any way to fix  it?
In system settings>power management, set the screen off to never.[/QUOTE]
No - I get the same issue as described above. Screen off is set to never (having previously tried 1 hour). Lock screen is turned off (having previously tried 1 hour after screen off). Either way the same thing happens - after about 10 minutes the screen turns off. This doesn't seem to happen while watching vids through XBMC even though I'm just running it as an app on top of Unity.

This also isn't the first time it's happened in Ubuntu - the screen power management showed the same bug about two or three releases ago and was only patched a few months into the release cycle.

Edit to add I've not found a workaround for this yet so probably shouldn't be posting in this thread, sorry!!

---

### Post by Stonecold1995 on 2012-11-04
> **Pyloo said:**
> No - I get the same issue as described above. Screen off is set to never (having previously tried 1 hour). Lock screen is turned off (having previously tried 1 hour after screen off). Either way the same thing happens - after about 10 minutes the screen turns off. This doesn't seem to happen while watching vids through XBMC even though I'm just running it as an app on top of Unity.

This also isn't the first time it's happened in Ubuntu - the screen power management showed the same bug about two or three releases ago and was only patched a few months into the release cycle.

Edit to add I've not found a workaround for this yet so probably shouldn't be posting in this thread, sorry!!

I think I may have had the same problem in Kubuntu.  What's the output of this?
```
xset -q
```

---

### Post by a-user on 2012-11-05
> **Pyloo said:**
> No - I get the same issue as described above. Screen off is set to never (having previously tried 1 hour). Lock screen is turned off (having previously tried 1 hour after screen off). Either way the same thing happens - after about 10 minutes the screen turns off. This doesn't seem to happen while watching vids through XBMC even though I'm just running it as an app on top of Unity.

This also isn't the first time it's happened in Ubuntu - the screen power management showed the same bug about two or three releases ago and was only patched a few months into the release cycle.

Edit to add I've not found a workaround for this yet so probably shouldn't be posting in this thread, sorry!!

most probably your xscreen saver is giving you a black screen after w while.

try this:
xset s off

to make this permanently you have to add it to your xinitrc.

this annoyed the hell out of me until i discovered this.

---

### Post by philinux on 2012-11-05
Wobbly windows and other effects are not installed in the default install.

```
sudo apt-get install compiz-plugins-extra
```

Will solve this. As always be careful with compizconfig-settings-manager which by the way needs to be installed too if you haven't done so already.

[edit] you'll need to either log out and back in or use the code setsid unity to see the changes take effect.

---

### Post by DGINSD on 2012-11-07
> **Stonecold1995 said:**
> I think I may have had the same problem in Kubuntu.  What's the output of this?
```
xset -q
```

Here's my output for xset still shows a 10 minute screen saver even though it's set to never. How do I change that? 

```
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  7/2    threshold:  7
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

---

### Post by Cavsfan on 2012-11-09
Quantal Quetzel does not display the date in the upper right hand corner.

The workaround for that using dconf-editor is [[COLOR=blue]_here._[/COLOR]]("http://askubuntu.com/questions/129985/how-to-make-the-date-appear-next-to-the-time-indicator-in-gnome-classic")

---

### Post by erythros on 2012-11-13
I´m sorry. I don´t usually ask for help in forums. I´m usually able to solve my issues via google searches, but in this case I have tried various search parameters and have failed to find anyone else discussing that same problem I have currently.

I did a clean install of 12.10 on two separate computers and am experiencing on at least one of them the following issue:

I need to press certain keys twice for an input to appear.
Here is a sort list of characters that i have to enter twice in order to display once:

´
¨
^
`
~

---

### Post by erythros on 2012-11-13
Turns out I'm an idiot... Under keyboard layout, there was a selected variant: English (US, alternative international). I must have accidentally selected it during install, and didn't notice until certain passwords were failing... 

> **erythros said:**
> I´m sorry. I don´t usually ask for help in forums. I´m usually able to solve my issues via google searches, but in this case I have tried various search parameters and have failed to find anyone else discussing that same problem I have currently.

I did a clean install of 12.10 on two separate computers and am experiencing on at least one of them the following issue:

I need to press certain keys twice for an input to appear.
Here is a sort list of characters that i have to enter twice in order to display once:

´
¨
^
`
~

---

### Post by Cavsfan on 2012-11-14
> **erythros said:**
> Turns out I'm an idiot... Under keyboard layout, there was a selected variant: English (US, alternative international). I must have accidentally selected it during install, and didn't notice until certain passwords were failing...

No one is an idiot my friend. Every one of us has made mistakes at least those who have ever tried to do anything in Linux/Ubuntu.
There are people on this forum with varying degrees of knowledge but, I don't think anyone knows absolutely everything about everything. 
The key is to keep an open mind.
Glad you resolved your own problem. I have done that a lot myself after opening up a thread.

---

### Post by Carl H on 2012-12-10
Xubuntu 12.10 64bit. 

XFBurn does not run when selected from the menu. After a few seconds a crash report is generated. 

It can be made to run from a terminal with 

```
sudo xfburn
```

---

### Post by leogomes001 on 2012-12-11
I'm new here and I've updated from 12.04 LTS to 12.10 and now the game "Wakfu" isn't starting anymore like it was before the dist update. Now when I run the game and choose "play" the window closes.

 glxinfo | grep -i opengl:
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.1, 128 bits)
OpenGL version string: 2.1 Mesa 9.1-devel (git-64e9ec6 precise-oibaf-ppa)
OpenGL shading language version string: 1.20
OpenGL extensions:

I think that the problem is VMware, because before the update it was Xorg, but I'm not certain. Does somebody know how to fix it without a downgrade?

Thank you guys

---

### Post by Cavsfan on 2012-12-11
> **leogomes001 said:**
> I'm new here and I've updated from 12.04 LTS to 12.10 and now the game "Wakfu" isn't starting anymore like it was before the dist update. Now when I run the game and choose "play" the window closes.

 glxinfo | grep -i opengl:
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.1, 128 bits)
OpenGL version string: 2.1 Mesa 9.1-devel (git-64e9ec6 precise-oibaf-ppa)
OpenGL shading language version string: 1.20
OpenGL extensions:

I think that the problem is VMware, because before the update it was Xorg, but I'm not certain. Does somebody know how to fix it without a downgrade?

Thank you guys


**leogomes001**, you need to open your own thread in general help. This thread is just for known workarounds for problems in Quantal.
Thanks

---

### Post by leogomes001 on 2012-12-11
> **Cavsfan said:**
> **leogomes001**, you need to open your own thread in general help. This thread is just for known workarounds for problems in Quantal.
Thanks
okay, thanks.

---

### Post by Cavsfan on 2012-12-19
I mainly use Gnome Classic with Cairo Dock, Emerald and Compiz but, it seemed everytime I logged in to Quantal I would be looking at a black box around Cairo Dock.

I could logout and back in a couple of times and that usually fixed it but, I finally figured out a way to fix it once and for all.

I have created 3 startup applications:

1) for Cairo Dock **cairo-dock -o -w 7** forcing it to wait 7 seconds before startup.

2) for Emerald I just use the standard **emerald --replace**

3) for Compiz I created a small script and put this in for the command **./home/cavsfan/compiz-script**

The script just contains this:
```
#! /bin/bash
sleep 5
compiz --replace
```

Copy that into a text editor and save it as **compiz-script** in your home directory.

I made the script executable via this entered in terminal **chmod +x ~/compiz-script**

I have never had a startup problem since.
(This also works on Raring Ringtail as it had the same black box startup problem.)

---

### Post by jcobban on 2012-12-20
> **mc4man said:**
> There seems to be an issue on fresh & maybe upgrade installs when installing any of the nvidia-* drivers.(& probably also  fglrx is the same
linux-headers-generic (linux-headers-3.5.0-17-generic) is not default installed & will not be installed when installing the nvidia-* package
(I believe the dep is improperly satisfied by linux-headers which is default installed

This will cause the kernel module not to be built & when rebooting users will not get a fully working Desktop.

So before installing any of the nvidia drivers or fglrx best to - 
```
sudo apt-get install linux-headers-generic
```

Edit:
It's been decided not to adjust the nvidia-* or fglrx packages so people need to do as above or maybe complain on this bug

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)

I followed this advice and fixed the problem that my laptop would not resume when opened after installing 12.10.  However it was not clear either from here, or from any other response to a google search, how to install and activate the proprietary driver.  Most of the web sites documented how you did it in older releases.  Using the dash returned no meaningful response to either "hardware" or "drivers".  To me it is not intuitively obvious that you should click on "Software Sources" to update these drivers.  In my opinion this capability has been integrated into an inappropriate tool or alternatively the dash should respond meaningfully to a search for hardware drivers.

---

### Post by timgood on 2012-12-21
> **jcobban said:**
> I followed this advice and fixed the problem that my laptop would not resume when opened after installing 12.10.  However it was not clear either from here, or from any other response to a google search, how to install and activate the proprietary driver.  Most of the web sites documented how you did it in older releases.  Using the dash returned no meaningful response to either "hardware" or "drivers".  To me it is not intuitively obvious that you should click on "Software Sources" to update these drivers.  In my opinion this capability has been integrated into an inappropriate tool or alternatively the dash should respond meaningfully to a search for hardware drivers.

I heartily concur.

---

### Post by Sandor1 on 2013-01-02
Hello Friends!

I've got a little problem after getting the upgrade. Sometimes the white little arrow before a shortcut on the launcher starts blinking rapidly for no reason I am aware of, so it locks the system. If I succeed to quit the programme, the same things happens to another, so at the end it only lasts for me to restart the system. Are there any solutions for that? ):P

Thanks a lot!

Best.

---

### Post by wojox on 2013-01-02
> **Sandor1 said:**
> Hello Friends!

Sometimes the white little arrow before a shortcut on the launcher starts blinking rapidly for no reason I am aware of, so it locks the system. 

This happened to me last weekend or the week before. A Compiz update the following Monday fixed it. Try fully updating again and reboot.

---

### Post by cabz on 2013-01-06
I had a major issue trying to install google earth in a fresh 12.10 wubi install. 
it seems that  when doing a 12.10 only install and not a 12.04 upgrade you loose ia32-libs-multiarch files causeing google earth/wine and skype to name a few to not be able to be installed .Here is a link to the the thread . i hope this helps someone else to not loose as much hair as i did.:p
[http://ubuntuforums.org/showthread.php?t=2100827](http://ubuntuforums.org/showthread.php?t=2100827)

---

### Post by tad1073 on 2013-01-15
Online accounts crashes when trying to log into facebook, twitter and flikr, gmail works fine.

When I try to enter user name I get logged out.

---

### Post by Cavsfan on 2013-01-15
> **tad1073 said:**
> Online accounts crashes when trying to log into facebook, twitter and flikr, gmail works fine.

When I try to enter user name I get logged out.

That sounds like something you should open a thread in general help for. This is for problems and the known workaround for that problem.

---

### Post by tad1073 on 2013-01-15
> **Cavsfan said:**
> That sounds like something you should open a thread in general help for. This is for problems and the known workaround for that problem.

gotcha

---

### Post by melitz on 2013-02-09
> **timgood said:**
> If you are suffering distorted 'scratchy' sound with Skype 4 you can fix it by: 
```
gksu gedit /etc/pulse/default.pa
```and changing the line: load-module module-udev-detect
to: load-module module-udev-detect tsched=0

Sound will be OK after reboot.

Hope this helps.

Worked like a charm!!! Thanks!!\\:D/

---

### Post by ryanormrod on 2013-02-13
If you have a HP G6 Pavilion laptop you may run into an issue when attempting to install. Particularly, the screen will lock because of the way the kernel tries to load a fancy boot screen but the graphics can't load it (as far as I understand the problem) 

Solution:
1) Restart and load DVD and hit space as soon as you see a keyboard sign.

2) Select language and press F6, you need to select nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

3) Continue to install but bare in mind that after you install you must edit the grub at boot. Select ubuntu from the Grub boot menu, press the edit key(E) and add after see the link I posted above.

4) When you have installed and got booted into your graphical interface, apply any updates, then go to "software sources" -> "additional drivers" and select a proprietary drives from the list. (The open driver was too slow for me). 

5) Once it installs the driver, restart and you should be enjoying Ubuntu 12.10.

---

### Post by tkruise on 2013-02-19
Can't seem to get any partition program to function.. GParted doesn't work within Quantal ambient..

---

### Post by bogan on 2013-02-19
> **tkruise said:**
> Can't seem to get any partition program to function.. GParted doesn't work within Quantal ambient..Please create your own new Thread, probably best in the Absolute Beginners forum, and give your set-up details, and which "partition programs" are affected.

This is a thread for describing work-arounds and solutions for Known BUGS, AS THE TITLE SAYS.

**bogan**.

---

### Post by hawthornso23 on 2013-02-20
> **bogan said:**
> 

This is a thread for describing work-arounds and solutions for Known BUGS, AS THE TITLE SAYS.

**bogan**.

Actually the title says it is for "Know bugs".

And since I find myself in the process of making a metacomment on this thread, could I also request that the "Known bugs" thread for the LTS version be restored. Many of us are still running it. After all LTS stands for "long term SUPPORT". The known bugs thread is a very useful form of support in my opinion. Why such haste to drop it?

---

### Post by Cavsfan on 2013-02-21
> **bogan said:**
> Please create your own new Thread, probably best in the Absolute Beginners forum, and give your set-up details, and which "partition programs" are affected.

This is a thread for describing work-arounds and solutions for Known BUGS, AS THE TITLE SAYS.

**bogan**.

> **hawthornso23 said:**
> Actually the title says it is for "Know bugs".

And since I find myself in the process of making a metacomment on this thread, could I also request that the "Known bugs" thread for the LTS version be restored. Many of us are still running it. After all LTS stands for "long term SUPPORT". The known bugs thread is a very useful form of support in my opinion. Why such haste to drop it?

Actually that is a typo: it should say Known and not Know. Go back to the very first post and read that.
I was going to suggest that you open your own thread in the Absolute Beginners forum myself but Bogan beat me to it.

Here is the Precise Pangolin 12.04 LTS thread:

[[COLOR=blue]_Precise known bugs with workarounds_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1968155")

That _should_ be made into a sticky so people can find it.

---

### Post by pme 72 on 2013-02-22
Issue: labored Unity performance after Resume from Suspend with Radeon HD4550 GPU (RV710)
Resolution: close any open programs and run sudo restart lightdm in a terminal. 

My older ATI Radeon X1550 (RV505) does not appear to have the same issue.

---

### Post by Cavsfan on 2013-03-12
> **mc4man said:**
> There seems to be an issue on fresh & maybe upgrade installs when installing any of the nvidia-* drivers.(& probably also  fglrx is the same
linux-headers-generic (linux-headers-3.5.0-17-generic) is not default installed & will not be installed when installing the nvidia-* package
(I believe the dep is improperly satisfied by linux-headers which is default installed

This will cause the kernel module not to be built & when rebooting users will not get a fully working Desktop.

So before installing any of the nvidia drivers or fglrx best to - 
```
sudo apt-get install linux-headers-generic
```

Edit:
It's been decided not to adjust the nvidia-* or fglrx packages so people need to do as above or maybe complain on this bug

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)

Thank you much mc4man! My quantal install went bad for some reason and I tried to do a clean install twice. The first time I did not see your post and lost the 1st attempt at a clean install.
I had a 2nd unusable desktop.
The 2nd time I installed linux-headers-generic, rebooted and installed nvidia-current-updates and all went well finally!
I added my name to that bug and then it said it was a duplicate of this one:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1070427](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1070427)

So, I added my name to that one too. It said that it had been fixed in Precise and Raring but, in Quantal it has been Triaged.
Now, I'll finally have my Quantal install back. :popcorn:

---

### Post by NikiNfOuR on 2013-03-26
When i installed the ubuntu gnome remix edition 12.10.1, there was no **Ubuntu Software Centre **and also the **Software Updater** and it was not possible to install the software through the terminal too.


[B]SOLUTION :
[/B]
sudo apt-get -f install

sudo apt-get update


After this i was able to install the ubuntu software centre through terminal :)

---

### Post by CamPsych on 2013-03-29
HI all, 

I am running into issues with Sandy Bridges GPU and system hang (every couple of hours especially when a several apps running at a time, usually Thunderbird and Firefox) and I have seen on the forums that a few others are getting the same issue. Apparently this is a known bug with Debian [http://lists.debian.org/debian-x/2012/01/msg00250.html](http://lists.debian.org/debian-x/2012/01/msg00250.html) but I can't seem to find anything with 12.10 and a workaround. 

Is this a bug of 12.10 and is there a workaround, or am I best to install a different distro? 
Very noob here, so apologies if I am posting in wrong place or not giving right amount of info. 

Cheers

---

### Post by matt_symes on 2013-03-29
Hi

> **CamPsych said:**
> HI all, 

I am running into issues with Sandy Bridges GPU and system hang (every couple of hours especially when a several apps running at a time, usually Thunderbird and Firefox) and I have seen on the forums that a few others are getting the same issue. Apparently this is a known bug with Debian [http://lists.debian.org/debian-x/2012/01/msg00250.html](http://lists.debian.org/debian-x/2012/01/msg00250.html) but I can't seem to find anything with 12.10 and a workaround. 

Is this a bug of 12.10 and is there a workaround, or am I best to install a different distro? 
Very noob here, so apologies if I am posting in wrong place or not giving right amount of info. 

Cheers

Sandy bridge with an Intel graphics card ?

If so then look towards the end of this thread

[http://ubuntuforums.org/showthread.php?t=2127593](http://ubuntuforums.org/showthread.php?t=2127593)

Check to see if you have the same graphics card (check the cards vendor id and device id and revision number) and are getting the same errors. 

If so try out the proposed solution of updating the kernel.

Kind regards

---

### Post by Linuxisfast on 2013-03-29
Strange I have second generation icore 5 laptop and never ever faced this issue either with 12.04 or 12.10, I suggest you install two ppas namely x-swat and ppa glasen/intel-drivers which will install all the latest files for your intel Sandybridge card. Hopefully this will resolve all your issues. Do make sure you are running the latest BIOS.

---

### Post by Bulldogslaxxman12 on 2013-04-01
Thanks will do

---

### Post by CamPsych on 2013-04-02
@matt_symes and @linuxisfast - seems that those fixed the issue that I was having, looks like a lot of other users here too the same with the amount of threads on same issues.

---

### Post by anhmaphptn on 2013-04-03
not sure that is a true

---

### Post by kOvaxo on 2013-04-11
After updating kenral via software updater no kenral header being installed with NEW kernal , always the stuck with the old header ,so had to update it manual to get my video card work properly .

[HTML]sudo apt-get install linux-headers-$(uname -r)[/HTML]

---

