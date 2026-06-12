---
title: "radeon ati power saving"
date: 2012-10-24
forum: General Help
---

### Post by sebastian3310 on 2012-10-24
Hi everybody,
i've just passed to Ubuntu 12.10. I had windows 7 before. The problem is that now the pc is overheating and this is because of the GPU. On windows i could switch to "power saving" GPU but now i CANT. I've read that the solution is executing this 2 lines:
 echo profile > /sys/class/drm/card0/device/power_method
 echo  low > /sys/class/drm/card0/device/power_profile

but i got: "Not such file or directory" because this files dont exist on the file system. Anybody has tha same problem or know the answer? THANKS A LOT

---

### Post by jonnyboysmithy on 2012-10-24
Hi, I also have switchable graphics on my system, it also got really hot.

I had the same problem: 'no such file or directory' when  I did the command.
A clean install fixed it for me (I think something changes when you install a driver).
Anyway test it on a livecd/liveusb and see if that works if it does then you might want to do a reinstall.
 It did the trick for me :)

---

### Post by jonnyboysmithy on 2012-10-24
These are the instructions I followed:
> I have an HP dv7-6b78us with hybrid graphics - an ATI Radeon and an Intel graphics card.
 They're both on by default and the Intel is more than enough power for my use. 
Here's how I managed to turn off the Radeon and save massive battery life:

First, make sure you've uninstalled any proprietary graphics drivers. 
There's a proprietary driver thingy in the administrative menu for that.

Next, add these to /etc/rc.local above the 'exit 0' line (e.g. sudo nano /etc/rc.local from the terminal):
```
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```And then add this to /etc/modprobe.d/blacklist-local.conf, also as sudo:
```

blacklist fglrx

```Reboot. Verify by doing the following:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```You should see something like this:
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

```IGD is the Intel chip, the + means it's the one in use, and Pwr means it's on.
 DIS is the ATI card and if it says Off, you're saving a ton of battery.

This is a permanent fix that lasts across reboots.

Let us know how it goes :)

---

### Post by sebastian3310 on 2012-10-25
Hi Johny, thanks for your answer. But i dont want to switch the graphic card from radeon to Inten, i just have readeon on my pc. I want to tell radeon to work with LESS POWER and avoid overheating!! maybe i dont find the files: power_profile and power_method because i dont have installed the open source driver???? how can i do that?? Please help!!!!

---

### Post by mastablasta on 2012-10-25
what are the system specs?

---

### Post by jonnyboysmithy on 2012-10-25
What graphics card do you have? if you do ```
lspci
``` in the terminal it will spit out a list of devices attached to your computer. If you do ```
lspci | grep "ATI"
``` it will only grap lines with the word ATI. Anyway that should let you know what card you have. As for the driver search for it in synaptic package manager and simply install the package (at least I think its that simple). Not sure what package you need but we can look into it when we know what card you have. 

As for the no such file or directory error I'm stumped. You could try run the command on a livecd just to see if it works on a fresh system.

---

### Post by Psychobudgie on 2012-10-25
I use AMDOverdriveCTRL which you can pickup from

[http://sourceforge.net/projects/amdovdrvctrl/](http://sourceforge.net/projects/amdovdrvctrl/)

It works like a charm with my 6770. I have 2 profiles saved, 1 low and 1 medium and use it's bezier model for FanCtrl. I keep it on low for desktop and my GPU temp is identical to windows 7. 

Before installing my GPU was hitting 70 degrees and up on normal desktop usage.

Just make a note of low settings and set medium and high to match and save them as a power save or desktop profile and load them when it starts. Should sort things out for you. Oh I'm using the AMD Drivers and not the Open Source ones.

---

### Post by sebastian3310 on 2012-10-25
Hi psychobudgie,
i tried the program but it says driver catalyst is not installed..should i install them?
This is the output of the command: lspci | grep "ATI":

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]


any idea??? my pc is burning ;(

---

### Post by mayagrafix on 2012-10-25
Ditto for me:

:>)@Inspiron-620s:~$ lspci | grep "ATI"

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Caicos HDMI Audio [Radeon HD 6400 Series]


:>)@Inspiron-620s:~$ AMDOverdriveCtrl

ERR: Error: Could not Init library.
WRN: Adapter index out of range. Index forced to zero.
INF: Adapter index 0 choosen.
INF: Nr. of Performance Levels: 0
ERR: ADL does not report default performance levels.

---

### Post by jonnyboysmithy on 2012-10-26
The open source drivers are known for getting reallly hot.
Thanks for the info Psychobudgie! Thanks a lot. :)
 I  also have an Radeon 6700M with switchable graphics and found the only  solution to be to not use the 6700m and switch to integrated. I may use  the Radeon after all :)
Psychobudgie do you have catalyst installed?
@Sebastian you can get catalyst control centre from amds website with their proprietary driver with which I have had no luck.

---

### Post by Psychobudgie on 2012-10-26
I'm using the catalyst drivers and NOT the open source ones. The Open Source drivers result in most AMD cards combusting or the fans taking flight.

The safest option is to go to system settings > software sources > additional drivers and select fglrx(proprietary). Let Ubuntu install and reboot. You should immediately notice that the fans no longer sound like a jet aircraft. Then run AMDOverdriveCTRL and set the medium and high settings to match the low and press SET. Go to the FanCtrl tab and set it to bezier and enable it. Save the profile and watch the temperature of your processor drop like a stone. Then hit TaskBar and leave it running in the background. 

You may have to input the following into a terminal to allow you to see/interact with the panel icon.

gsettings set com.canonical.Unity.Panel systray-whitelist "['AMDOverdriveCtrl']"

once added you will have to restart the session.

---

### Post by mayagrafix on 2012-10-27
Ubuntu 12.10 Unity Desktop does not show after I installed ATI drivers

I went to system settings > software sources > additional drivers and selected fglrx(proprietary) ATI drivers.

After installed I reboot and no Unity interface, very slow to move windows around desktop.

Able to open terminal and execute commands like firefox, which is how Im writing this.

How can I execute from a terminal to open system settings, then Software Sources, then additional drivers and revert to open source drivers?

or what is the best way to fix this?

Thanks for any and all help

---

### Post by Linuxisfast on 2012-10-27
> **mayagrafix said:**
> Ubuntu 12.10 Unity Desktop does not show after I installed ATI drivers

I went to system settings > software sources > additional drivers and selected fglrx(proprietary) ATI drivers.

After installed I reboot and no Unity interface, very slow to move windows around desktop.

Able to open terminal and execute commands like firefox, which is how Im writing this.

How can I execute from a terminal to open system settings, then Software Sources, then additional drivers and revert to open source drivers?

or what is the best way to fix this?

Thanks for any and all help

sudo apt-get install linux-headers-generic


sudo apt-get purge fglrx*

sudo apt-get install fglrx

sudo aticonfig --install

reboot.

---

### Post by mayagrafix on 2012-10-27
Thanks for your promt responce. 
> sudo apt-get purge fglrx*

sudo apt-get install fglrx

sudo aticonfig --install

reboot. 
From these commands I sumise that I would be re-installing the propietary ATI drivers? 

In the meantime I found this tread and as per instructions removed and re installed Open SOurce drivers. My desktop is back to normal (Unity is up and running).

[http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu](http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu)

However, how do I know if Im running the latest and greates Open Source drivers? the tread mentioned is for 11.04 and dated back to 2011. 

> Revert back to the open source drivers
After installing drivers from deb packages

**Remove all the fglrx traces from your system:**

sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

**Remove your xorg.conf**

sudo rm /etc/X11/xorg.conf

**Reinstall xorg**

For 32bits systems

sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri

For 64bits systems

sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core

**Configure Xorg**

sudo dpkg-reconfigure xserver-xorg

**Reboot:**

sudo reboot

After the reboot all the fglrx packages will be gone, you will be using default ones.
Will the Updater software automatically try to install the newest Xorg drivers?

Thanks for any and all help:KS

---

