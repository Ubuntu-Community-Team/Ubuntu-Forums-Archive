---
title: "Disable laptop touch pad permanently"
date: 2019-02-05
forum: General Help
---

### Post by jek1 on 2019-02-05
Ubuntu 14.04 LTS

Is there any way that you can disable the laptop touch pad permanently so that it does not come on every time you log out or unplug the mouse? Can you for example run the System Settings as root (sudo) and disable it there? Would that do the trick?

---

### Post by #&amp;thj^% on 2019-02-05
This "should" get you what you want:
```

xinput set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0
```

And if you decide to revert it use:
```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 1
```
but you will have to reboot to set the change.
Or you can even use for the session.:
```
synclient TouchpadOff=0
```

To revert:
```
synclient TouchpadOff=1
```

---

### Post by jek1 on 2019-02-05
Thanks 1fallen, but that did not make any difference. The touch pad is still reactivated the moment I unplug the mouse, and also when I log out.

---

### Post by #&amp;thj^% on 2019-02-05
> **jek1 said:**
> Thanks 1fallen, but that did not make any difference. The touch pad is still reactivated the moment I unplug the mouse, and also when I log out.

he he, Which command reactivates the touchpad?
"synclient TouchpadOff=0" only lasts for a session.

---

### Post by jek1 on 2019-02-05
Unplugging the mouse reactivates it - I don't want that.
Logging out to log into another account reactivates it - I don't want that.

---

### Post by #&amp;thj^% on 2019-02-05
Again, I asked which command's have you used.
it's clear to me that "You don't want that. "
You may need to  install "xserver-xorg-input-synaptics"

---

### Post by jek1 on 2019-02-06
I do realise that "synclient TouchpadOff=0" only lasts for a session. I have not tried that because that won't solve my problem. I have however tried

xinput set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0

and that did not make any difference.

---

### Post by jek1 on 2019-02-06
I have also checked now, "xserver-xorg-input-synaptics" isalready installed.

---

### Post by mc4man on 2019-02-06
Logging out shouldn't have any effect. If the touchpad is disabled in system settings it should survive log out or reboots.

However in 14.04 > 16.04 when there is a disabled touchpad with a usb mouse if the mouse is disconnected the touchpad usually is auto re-enabled.  That would be the expected and probably proper behavior.
Somewhere between 16.04 and 18.04 this stopped happening. 
So now, (18.04 and +) once disabled it should stay disabled irregardless of the usb mouse state. From some perspective this would be a bug..

---

### Post by #&amp;thj^% on 2019-02-06
I couldn't agree more with mc4man.;)
Have you tried to install Touchpad Indicator It requires adding a PPA to get it though.(Some Folks don't want to add outside sources for needed software)
PPA found here:[https://launchpad.net/~atareao/+archive/ubuntu/atareao](https://launchpad.net/~atareao/+archive/ubuntu/atareao)
```

sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

it will:

[list][*]Disable / Enable touchpad with indicator menu or keyboard shortcut.

    [*]Disable touchpad when mouse is plugged.
    [*]Disable touchpad while typing.[/list]

Hope it helps

---

### Post by jek1 on 2019-02-07
Thanks 1fallen. I have attempted to install touchpad-indicator as it looks like it would solve my problem. However I get the following error output while installing:

dpkg-deb: error: archive '/home/jek/.installed-jek/20190207-touchpad-indicator/touchpad-indicator_2.1.3-0extras18.04.0_all.deb' has premature member 'control.tar.xz' before 'control.tar.gz', giving up
dpkg: error processing archive /home/jek/.installed-jek/20190207-touchpad-indicator/touchpad-indicator_2.1.3-0extras18.04.0_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2


What does this mean and what can I do to correct it?

---

### Post by #&amp;thj^% on 2019-02-07
That's one I have not seen before.
can you tell me how you tried to install it exactly?
Needed information is commands used.

---

### Post by jek1 on 2019-02-08
1fallen, At first I installed it as you described above. I did not notice the error message then and closed the terminal before I could copy it. However it did not work and looked as if it was not installed at all so I decided to install it again. So as not to waste internet data on downloads, I copied the .deb packages listed below

from /var/cache/apt/archives/
to /home/jek/.installed-jek/20190207-touchpad-indicator/

and installed it from there with

sudo dpkg -i -R /home/jek/.installed-jek/20190207-touchpad-indicator/

The .deb packages copied is

gir1.2-gconf-2.0_3.2.6-0ubuntu2_amd64.deb
gir1.2-rsvg-2.0_2.40.2-1_amd64.deb
python3-pyudev_0.16.1-2build1_all.deb
python3-xlib_0.14+20091101-1ubuntu2_all.deb
touchpad-indicator_2.1.3-0extras18.04.0_all.deb

---

### Post by #&amp;thj^% on 2019-02-08
Creative, I'll give you that. :)
But it would be better if i could see that output from:
```
sudo apt install --reinstall touchpad-indicator
```
lets start from there first.

---

### Post by jek1 on 2019-02-08
Full output from that (exactly the same error message):

jek@jek-Inspiron-3558:~$ sudo apt install --reinstall touchpad-indicator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  touchpad-indicator
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/398 kB of archives.
After this operation, 1 483 kB of additional disk space will be used.
dpkg-deb: error: archive '/var/cache/apt/archives/touchpad-indicator_2.1.3-0extras18.04.0_all.deb' has premature member 'control.tar.xz' before 'control.tar.gz', giving up
dpkg: error processing archive /var/cache/apt/archives/touchpad-indicator_2.1.3-0extras18.04.0_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/touchpad-indicator_2.1.3-0extras18.04.0_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by #&amp;thj^% on 2019-02-08
Well then, we'll just get rid of it.
```
sudo apt remove --purge touchpad-indicator
```
followed with:
```
sudo apt autoremove
```
Also remove the PPA from your sources.
Also let's check the package-manager with:
```
sudo apt update
sudo apt upgrade
```
make sure we see NO new errors.
Sorry my friend,

---

### Post by jek1 on 2019-02-09
Thanks 1fallen and sorry for all the trouble I caused you.

---

### Post by mc4man on 2019-02-09
The error  on installing is seen by 14.04 users with an older dpkg,
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1730627](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1730627)

---

### Post by #&amp;thj^% on 2019-02-09
Thanks mc4man I had also seen that bug report yesterday googling.
I just did not want to recommend/suggest that jek1 install the "bionic dpkg".
I would also like him to try from terminal:
```
gsettings set org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled false
```
if that works, >>Adding this
```

/bin/bash -c "sleep 15 && gsettings set org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled false" 
```
to Startup Applications will also permanently disable the touchpad.

---

### Post by mc4man on 2019-02-09
> **1fallen said:**
> Thanks mc4man I had also seen that bug report yesterday googling.
I just did not want to recommend/suggest that jek1 install the "bionic dpkg".
I would also like him to try from terminal:
```
gsettings set org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled false
```
if that works, >>Adding this
```

/bin/bash -c "sleep 15 && gsettings set org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled false" 
```
to Startup Applications will also permanently disable the touchpad.

It was fixed in 14.04, i.e,
> dpkg (1.17.5ubuntu5.8) trusty; urgency=medium

  * Add support for .deb archives with a control member not compressed
    (control.tar) or compressed with xz (control.tar.xz) LP: #1730627.

 -- Adam Conrad <adconrad@ubuntu.com> Mon, 04 Dec 2017 12:15:45 -0700

Had this come up a couple of weeks ago via launchpad mail concerning a 14.04 mpv package. The user was quite behind on updates..
Additionally it seems users quite often disable the -updates & or -security repos for whatever reason..

---

### Post by jek1 on 2019-02-19
Thanks mc4man, you finally got me on the right track to get touchpad-indicator working. All you need to do is upgrade dpkg to the latest version first (apt install dpkg) and then install touchpad-indicator again with dpkg. I now have a working touchpad-indicator and that solved all my touchpad problems.

And yes, I am one of those users who disabled all automatic updates. The reason is that those updates are quite heavy on internet data and I do not have an unlimmited supply of data. I have checked and to do all outstanding updates now will cost me almost half a gigabyte of data. That is 25 % of my monthly quota.

---

