---
title: "My day lost trying to make suspend behave properly"
date: 2008-02-23
forum: General Help
---

### Post by julien-1993 on 2008-02-23
I will try to make a long story short...

After 1 years on suse and 2 years now on ubuntu i finally decided to make an install without the Destop CD to have a more light and responsive system. So I decided to install from the scratch using a 7.10 Server 386 CD to try to obtain the sweetest box since a couple years on linux. 

I've installed with gnome-core package and slowly add and tune what was needed. i.e: eclipse, openoffice, deluge torrent, evince, cups, qalculate, gimp and totem

up to this point everything is pure ice cream.

couple of days later, tired from having to shut down everything each night and open everything in the morning and place all of them on the good workspace and open all my required files to work.....i'm doing a degree in I.T. engineering so it mean a good load of .doc and chart and web site and....well you see I need a good 5-10 minutes in the morning to open all my stuff and absolutely need to shut it down in the night to be able to sleep (very small room with 2 noisy box is no good)

Here I come to try enabling suspend and principally RESUME. wich I did not solved but came very close too... let me explain.

After clean install computer will suspend but hang on blank powered on screen.
Read about that on launch pad and forum and found that some succeed by adding ```
Option      "NvAGP"     "1"
``` to device section in xorg.conf

and 
```
SAVE_VBE_STATE=false
POST_VIDEO=false
```
to /etc/default/acpi-support

I then try these modification. Reboot , try to suspend and resume, Surprise it WORKED.....  what's the problem then ?you might say.  I lost AGP support...no more Nexuiz or any 3d game.

Why ? because by adding Option "NvAGP" "1" to xorg.conf I actually says to X to load nvidia-glx AGP driver at the same time with the standard agpgart AGP driver that is loaded as a kernell module. and that as the effect of causing an error wich result in not loading AGP support.

So I blacklisted the agpgart module from /etc/modprobe.d/blacklist. To this point AGP support is back with all its 3d gaming capabilities. But Resume from suspend is gone with the monitor that dont power on and keyboard and mouse not responding (but computer is on and i see some HD activity occasionally)

So up that point and late with the studies I decided to put back everything like it was in the beggining and just put a cross on the suspend features......I will wait till those bugs or problems are corrected officially.

If anybody knows how to activate this feature on a non-laptop computer while not creating other problems like the one I encounter, plllease helP :(

and sorry for the quality of my english, it is not my first language.

---

### Post by DaV|d on 2008-03-18
If you have an nvidia card (I'm assuming so), I had a very similar, if not the same problem.

Here's a workaround for **suspend to ram only**:

[LIST=1]
[*]I ran the following commands to remove all nvidia drivers and associated restricted modules:
```
sudo apt-get --purge remove nvidia-glx linux-restricted-modules-`uname -r` linux-restricted-modules-common
```

```
sudo apt-get --purge remove nvidia-glx-legacy nvidia-xconfig nvidia-settings linux-restricted-modules-`uname -r` linux-restricted-modules-common
```

[*]Installed the nvidia drivers with [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

[*]Added
```
Option      "NvAGP"     "1"
```
to the "Device" section in /etc/X11/xorg.conf

[*]Changed
```
SAVE_VBE_STATE=false
POST_VIDEO=false
```
in /etc/default/acpi-support.

[*]Blacklisted all modules displayed by
```
lsmod | grep agp
```
except for agpgart by adding
blacklist *module_name*
to /etc/modprobe.d/blacklist

for me it was 
```
blacklist sis_agp
```

[*]Renamed /usr/sbin/vbetool
```
sudo mv /usr/sbin/vbetool /usr/sbin/vbetool.bak
```
[/LIST]

Good luck! :)

---

