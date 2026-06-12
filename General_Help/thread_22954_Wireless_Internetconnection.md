---
title: "Wireless Internetconnection"
date: 2005-03-30
forum: General Help
---

### Post by SupahWoman on 2005-03-30
I don't know much about computers so I could use some help... I want to connect to the internet by a Wireless Connection. I have a Xircom card and I tried the wizard, but actually I don't know what to fill in.. So could someone be so nice to explain me what to fill in???? (step by step ==> dummie style plz!!!)

I also want my keyboard to be AZERTY and not QWERTY, where do I change that???

I hope you can help me!!!

Greetz,

Kim

---

### Post by az on 2005-03-31
More than half of the wireless cards have linux drivers available to them.  This is because either the manufacturer of the chipsets care enough about doing business with open source to provide the drivers or at least make it easy for developers to make them (by not hiding the specifications of their hardware)

I do not know what chipset your wireless device uses.  If the networking tool does not provide you with an option for wireless, it is probably beause you are using a card that does not have a driver made for it in Ubuntu.

You may use the windows driver to make your card work.  The software used is called ndiswrapper.  It can work with most windows drivers (but not all of them, although work is getting along quickly -  the version of ndiswrapper in Warty is significantly less advanced than the one in Hoary, and they are only six months apart)

There is no Graphical utility yet to use ndiswrapper.  You will have to use the command line to try your card.

I forget if ndiswrapper-utils is installed in Warty, if it is not, you will have to download the package and transfer it to your warty installation and install it first.
If you are using Hoary, you should be fine.  Just install ndiswrapper from synaptic package manager - the package is found on your cd.

Copy the Driver folder from the cd provided with your card to your Desktop.  Find a file named something that ends in .inf.

Open up a terminal (gnome-terminal) and type:
cd Desktop
cd Driver
cd (whatever folder you need to enter to get to the .inf file)
sudo ndiswrapper -i (filename.inf)
(enter your password)
ndiswrapper -l
(this will tell you what is installed)
sudo modprobe ndiswrapper

If it is successful, you will have a wireless device created in your /dev folder.  do:

iwconfig
to see a list of wireless devices available.  If you do not use a WEP, you can do

sudo dhclient wlan0 (if your device is named wlan0)

To try to connect to the internet.  If this is successful, run
sudo gedit
and add the word ndiswrapper to your /etc/modules file.  This will load the module at boot time, every time.  You should now be able to use the network tool to configure your wireless connection.

This will be less complicated eventually.
Good Luck.

---

### Post by gator64 on 2005-04-24
Hi,
I've been trying to get a wireless connection going with the Warty liveCD too.  I'm running into a few problems so far:  ndiswrapper-utils is not installed on Warty.  Now the easiest way to install it would be by downloading it, but since I'd need the wireless connection for that...

What I've done is gone into Windows, downloaded the ndiswrapper-utils onto my USB flash drive, which I can access fine from Warty.  But then, there are some problems with installation, such as recompiling the kernel.  This is my first try with Linux and with a live CD, so I'm not sure if what I want to do is possible or not:

What I'd like to do is make the USB drive a 'persistent home' and put together ndis-wrapper there.  My question is, am I going to run into problems adding the driver since I am running from the live CD?  I have no way of changing what's on the CD - will I be even be able to add ndiswrapper-utils?

---

