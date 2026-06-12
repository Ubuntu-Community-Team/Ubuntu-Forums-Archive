---
title: "Problems i encountered when first using ubuntu (and fixes)"
date: 2008-02-22
forum: General Help
---

### Post by tastybrains on 2008-02-22
Hello! 

I just installed Ubuntu 7.10, Gutsy Gibon, the other day after looking around for a newer version of linux than i was running - Fedora 7. I chose Ubuntu because more and more my Google search results for solutions to linux problems were turning up in this fantastically active forum. 

Here are some issues and their solutions I found after first starting to use ubuntu. They won't apply to everyone, but it might help someone like other people's posts helped me in my searches!

**Issue: **
LVM didn't work out of the box.
**[COLOR="SeaGreen"]Solution 1:[/COLOR]**
 - Use the alternate CD as the desktop version doesn't have it
**[COLOR="SeaGreen"]Solution2:[/COLOR]**
 - use apt-get to install lvm2. note, after installing using apt-get, lvm is not immediately available.  you'll need to either reboot (c'mon - isn't this why you ditched windows... ) or just type this to make lvm available:
 ```
sudo modprobe dm-mod
```


**Issue: **
my RAID card, 3ware 9550sx, worked perfectly out of the box from the base install, but the 3dm2 interface manager would not install. the error was "/etc/init.d/functions not found". the functions file is a redhat (maybe other too) specific file. 
**[COLOR="SeaGreen"]Solution:[/COLOR]**
Jonas Genannt has made versions of 3dm2 available as .deb files (what you need for ubuntu) [[COLOR="DarkOrange"]at his site[/COLOR]]("http://jonas.genannt.name"). download, install, done. 3ware also has a great [[COLOR="DarkOrange"]list of driver sources in their kb[/COLOR]]("http://www.3ware.com/kb/article.aspx?id=1456") if you need it:

**Issue: **
my netgear wn121t usb wireless device doesn't have drivers for linux, big surprise.
**[COLOR="SeaGreen"]Solution:[/COLOR]**
enter ndiswrapper. i followed [[COLOR="DarkOrange"]many[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3145540&postcount=3") [[COLOR="DarkOrange"]excellent [/COLOR]]("http://ubuntuforums.org/showthread.php?t=225206&highlight=install+wireless+manually")[[COLOR="DarkOrange"]guides[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=201902&highlight=install+wireless")on this site for installing the device. though they weren't for mine specifically, i learned alot about how ndiswrapper works and i can offer this advice:

[INDENT]1) download & compile your own version of ndiswrapper from the [[COLOR="DarkOrange"]project page[/COLOR]]("http://ndiswrapper.sourceforge.net/"). the one in the apt-get repository is usually not the latest version. there are tons of guides here how to do this. 

*hint:* i wasted lots of time trying to find & install the ndiswrapper-util package because it didn't show up in Synaptic package manager and the stuff i found going though dependency hell from installing each debian package individually. don't bother.just go the project page, download, install, and be done with it!

2) you need the driver file from your installer disc (*.inf files). they may be bundled in an *. exe executable file so you'll need to unpack it with either unzip, cabextract or another unpacker of your choice. 

*hint:*as i learned from the experienced wifi  users here, the version of your driver files &  ndiswrapper matter. i couldn't get the drivers included with my cd (to work with ndiswrapper, so i had to do some digging. 

2a) check the [[COLOR="DarkOrange"]ndiswrapper list[/COLOR]]("http://ndiswrapper.sourceforge.net/joomla/index.php%3F/component/option,com_openwiki/Itemid,33/id,list/&sa=X&oi=smap&resnum=1&ct=result&cd=5&usg=AFQjCNH4BK7WtsKDnlMhMDyDbuRjmCk_kA") for your usb device. Many devices use the same chipset, so if yours doesn't work with ndiswrapper, maybe one of the others does. My usb device is Netgear, but I ended up using the used the Topdog driver, netmw245.inf, from Marvell. 

2b) find out what USB id your device has by using: lsusb
this told me the wn121t ID was:
 0846:7100 netgear, inc

with those two pieces of information i Googled for the correct driver and found [[COLOR="DarkOrange"]this post[/COLOR]]("http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=938&Itemid=1") which confirmed that this would work. the link to the driver on opendrivers.com just took me in circles, so i googled for that driver by topdog and found a [[COLOR="DarkOrange"]link here[/COLOR]]("http://forums.driverguide.com/showthread.php?t=t=37046"). jackpot. version 1.0.4.9 works great.
 [/INDENT]


**Issue: **
Installing vmware server gave me some trouble. installer crapped out saying it couldn't copy a file or get access to something. When i tried again, the installer said the installation process has already started or something and wouldn't let me continue.
**[COLOR="SeaGreen"]Solution:[/COLOR]**
with ubuntu 7.10 you have to download the targzip'd file and install using vmware-install.pl rather than using an RPM like fedora. if you've tried to install once and now it won't let you begin the installation process again just cd into the bin folder where you are trying to run vmware-installer.pl and run the vmware-uninstaller.pl.

then follow [[COLOR="DarkOrange"]this guide[/COLOR]]("http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/"). in 3 steps you'll have it working.

**Issue: **
Hamachi wouldn't install. it didn't give an error, it just didn't do anything
**[COLOR="SeaGreen"]Solution:[/COLOR]**
Found the [[COLOR="DarkOrange"]solution here in the forums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=553774&highlight=gutsy+hamachi"). Turns out you just need to unpack the hamachi program using UPX.
then feel free to follow this to [[COLOR="DarkOrange"]secure your install and setting up hamachi as a service[/COLOR]]("http://www.computechgroup.com/?p=360") if you feel like it

well that's it for now. hope this might help someone :)

-tastybrains

---

### Post by fjgaude on 2008-02-22
Thanks for your first post... you made a wonderful Ubuntu user. You can, I'm sure, help many folks in the future with their problems, issues. Such a big world out there, and here.

---

