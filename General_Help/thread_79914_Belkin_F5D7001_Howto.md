---
title: "Belkin F5D7001 Howto"
date: 2005-10-21
forum: General Help
---

### Post by kisain on 2005-10-21
ok well here is my first how to ^_^ thats right i've enterd geekdom ^_^

Now this How to is gonna work for the model belkin F5D7001 Broadcom Chipset : BCM430 series cards and BCM4306KEB the cards which have these numbers seem to be supported and able to run in breezy with little trouble.
(NOTE:  This will not work on PPC and might work in a chroot envroment on amd64)
also this seems to work for Breezy Badger only.

1) open a Terminal and type "sudo gedit /etc/apt/sources.list

2) in the bottom of your sources.list paste this line with out the quoats:
"deb [http://ndiswrapper.sourceforge.net/debian](http://ndiswrapper.sourceforge.net/debian) ./" and save the file.

3) now in the same Terminal run " sudo apt-get update"  close terminal

4) open up synaptic and search for ndiswrapper and 2 pacages should show up
first make shure that the package "ndiswrapper-utils" is selected....now where gonna cheat a bit and also make shure that the "ndisgtk" package is also selected
now click apply ^_^

now while that is going on and it's dpwn loading the stuff you might as well get the files you will need and to do that go here : [http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)

now download this file to your desktop and place it in a folder called "drivers"
you'll see why in a minute ;D
--------------------------------------------------------------------------------------------------------
1) open up a Terminal and type: cd Desktop, then type cd drivers.

2) now that your in the drivers folder in the terminal type unzip {FILENAME}.exe
and boom you'll have a boat load of files popup in there.....look for a folder called "AR" and go into that dir by typeing cd AR ^_^

3) open up System > Administration > windows wireless Drivers
and a box will popup with a button that says "Install New Driver"

click on it and it will ask you where the .inf file is navigate till you get to the drivers folder on your desktop... and select the bcmwl5a.inf file

now click ok, now it should say in the box to the left " Hardware present:Yes"
now click Configure network.
--------------------------------------------------------------------------------------------------------
NETWORK SETUP:
now if you did this right you should have 3 connections in there now
a modem connection, an ethernet connecttion and a wireless connection. at least on my box i do lol ^_^

now keep this window open as you may need it.
1) click on the ethernet connection and click the Deactivate button to turn of eth0
(don't worry if anything goofs up you can just turn it back on ^_^

2) click on the wireless connection and select propertys

3) first click on Enable This connection, now type in your ESSID, change the key type (i chose hex) if your router has WEP enabled and then enter the WEP key where it says to. Under connection settings change the tab to DHCP

4) click ok

5) on wireless connection click the Activate button then click ok.

DONE!!!

now if you followed my instructions to the letter you will have a working wlan0 connection if you use some app like gkrellm you'll notice that the bandwith and stringth indecators are way off....it's a common glitch and besides that you have a working wireless connection who cares? ^_^

now i hope that this how to helps you out and makes it easyer for you to get your rather difficult card to work....
it took me 5 days to figure this out and it shoulden't for you. ^_^

if you have any info let me know and i will update this how to

kisain

---

### Post by Kamping_Kaiser on 2005-10-21
> **kisain]ok well here is my first how to ^_^ thats right i've enterd geekdom ^_^ [/QUOTE]
welcome  said:**
> 
Now this How to is gonna work for the model belkin F5D7001 Broadcom Chipset : BCM430 series cards and BCM4306KEB the cards which have these numbers seem to be supported and able to run in breezy with little trouble.
(NOTE:  This will not work on PPC and might work in a chroot envroment on amd64)

1) open a Terminal and type "sudo gedit /etc/apt/sources.list"


For the record (and you may want to change this), you should not use "sudo" to launch GUI applications. Use "gksudo"

> 
2) in the bottom of your sources.list paste this line with out the quoats:
"deb [http://ndiswrapper.sourceforge.net/debian](http://ndiswrapper.sourceforge.net/debian) ./" and save the file.

3) now in the same Terminal run " sudo apt-get update"  close terminal

you can also hit 'refresh' in synaptic :)
> 
4) open up synaptic and search for ndiswrapper and 2 pacages should show up
first make shure that the package "ndiswrapper-utils" is selected....now we're gonna cheat a bit and also make sure that the "ndisgtk" package is also selected. now click apply ^_^

now while that is going on and it's dpwn loading the stuff you might as well get the files you will need and to do that go here : [http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)

remember dial up may not be your friend trying to get several things at once :D

> 
now download this file to your desktop and place it in a folder called "drivers"
you'll see why in a minute ;D

<snip>
> 
NETWORK SETUP:
now if you did this right you should have 3 connections in there now
a modem connection, an ethernet connecttion and a wireless connection. at least on my box i do lol ^_^

now keep this window open as you may need it.

<snip>
> 
DONE!!!

now if you followed my instructions to the letter you will have a working wlan0 connection if you use some app like gkrellm you'll notice that the bandwith and stringth indecators are way off....it's a common glitch and besides that you have a working wireless connection who cares? ^_^

now i hope that this how to helps you out and makes it easyer for you to get your rather difficult card to work....
it took me 5 days to figure this out and it shoulden't for you. ^_^

if you have any info let me know and i will update this how to

kisain

just those 2 points from me, (dial up and sudo).
kk

---

