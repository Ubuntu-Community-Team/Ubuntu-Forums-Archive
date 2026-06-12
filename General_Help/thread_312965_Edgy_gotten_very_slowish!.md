---
title: "Edgy gotten very slowish!"
date: 2006-12-05
forum: General Help
---

### Post by xardas on 2006-12-05
For some reason. I have it installed on an Acer laptop with 1.7 Pentium M, 512MB RAM, 60GB HD. It was working fine but lately its gotten a little slow. When I click to start any application it takes a lot of time to load up. This is true even for a terminal or a folder link from a desktop. Anyone got any idea?

---

### Post by felixj on 2006-12-05
Check harddrive settings with
sudo hdparm /dev/YOUR_DEVICE (e.g. hda1)

Check if DMA is enabled and if the I/O-settings are 32bit-Mode.

There's HowTos around for using hdparm to tune your harddrives. Be careful, though.

---

### Post by Rodneyck on 2006-12-05
> **felixj said:**
> Check harddrive settings with
sudo hdparm /dev/YOUR_DEVICE (e.g. hda1)

Check if DMA is enabled and if the I/O-settings are 32bit-Mode.

There's HowTos around for using hdparm to tune your harddrives. Be careful, though.

Also check graphic drivers and make sure you have the latest. This can really slow everything down the menus and execution of applications, etc.

I have been running Edgy for awhile and no slow downs here, zips along in fact. People also report of crashes in Edgy. I have not had one, very stable.

---

### Post by Dual Cortex on 2006-12-05
Check the system monitor and see also see if there are any apps taking up CPU processing power.
e.g. the Nautilus 100% CPU bug.

---

### Post by Rodneyck on 2006-12-05
One other thing that coincides with the graphic drivers, make sure you specify a refresh rate in the Xorg.conf file. Most of the times it is not there.  This made my menus and applications open extremely fast. 

Here is how (open xorg.conf as root to make changes "gksudo nautilus")..

Open Xconf.org and under the following;

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"

Enter this and save...

HorizSync 30-100
VertRefresh 50-85

Or... Use this handy guide...

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by xardas on 2006-12-08
Are these settings applicable for my lcd screen too? It is a 15 inch lcd with max resolution of 1024.

---

### Post by Rodneyck on 2006-12-08
They should be fine, but the best thing to do is look up your monitor's specs either in its manual or online from the manufacturer. They usually list the exact horizontal and vertical specs. Just copy those in and save. Always back up your xorg.conf file though before changing.

The way Ubuntu works is it starts with the lowest refresh setting and works its way up to the highest for your monitor. LCDs I know can only do 75hz tops, at least they use to, unless that has changed recently.

---

### Post by xardas on 2006-12-17
Ok, I've changed the refresh rates but it hasnt worked. I think there's something wrong with gnome. It takes a long time to start up and then when I click to start on any applications it takes a long time for the application to start up. For a long time it just shows "starting application". 

Btw is there some kind of way to see what kind of services etc. are started or running in ubuntu?

---

### Post by Rodneyck on 2006-12-17
If you have automatrix2 installed, there is an option to install "ctrl, alt, delete" program which when used, will bring up a window showing what is running. This does not work under Beryl though. 

It may also be in synaptic, but not sure about that.

---

### Post by xardas on 2006-12-17
I think I had some kind of bootup manager installed in the previous version of ubuntu from which i could set the services i wanted to start etc. But I cant find it now.

---

### Post by kerry_s on 2006-12-17
Maybe try and do some basic clean up. 

Check in your home directory(hidden files) and delete all cache you can find.

sudo natilus /usr/share/doc   <-delete all contents, may take a while can be as large as 100mb

sudo natilus /usr/share/man   <-delete all contents, may take a while can be as large as 100mb

sudo natilus /usr/share/info   <-delete all contents

sudo natilus /var/log   <-delete everything but the folders, don't delete the folders

use synaptic and uninstall any extra kernels you might have and any apps you don't use/want

---

