---
title: "NetworkManager and Dialup connections"
date: 2006-11-12
forum: General Help
---

### Post by harty83 on 2006-11-12
When I right click on NetworkManager I see a Dial Up Connections menu with Connect to Modem and Disconnect from Modem.  How do you use this feature?  I click on connect to modem but nothing happens.  Where does network manager get its config for this?  I specifically want to use a cell phone modem that uses /dev/ttyACM0.  

Also, it seems that network-manager-openvpn will not install under Edgy because it requires libdbus-1.2.  Any clue how to get around this?

Thanks!
Alan

---

### Post by autocrosser on 2006-11-12
That is configured thru Menu>System>Networking(this is for Edgy--but the basics are the same)--tic on the Modem connection/properties & input the info & your set-up.

---

### Post by harty83 on 2006-11-12
Okay, I couldn't get the modem to connect using the system->administration->networking so I ended up editing /etc/network/interfaces to show the following

```
iface ppp0 inet ppp
provider verizon

```

I already had things working through pon/poff and my peer file I created.  I just wanted a gui way to connect/disconnect.  NetworkManager will now initiate and disconnect for me.  However, is it suppose to show that you are connected like it does with a wired or wireless connection?  Right now it does not.  It indicates that nothing is connected.

Thanks!

---

### Post by autocrosser on 2006-11-12
I use Gnome-PPP as far as connection--you can also add Modem Monitor to a panel (it uses network manager--Gnome-PPP sets up thru WvDial).

---

### Post by fragos on 2006-11-12
Perhaps the Modem Monitor panel applet would be helpul.  The Network Monitor one sure is with my broadband modem over Ethernet.

---

### Post by harty83 on 2006-11-12
I can't get gnome's built in dial up modem admin to work with my cell phone so I have to use a manually created peer file.  Is there a way to tell gnome-ppp to use a manually created peer file rather than create its own each time?

I can get kppp to work but it sometimes has issues running under gnome.

---

### Post by autocrosser on 2006-11-12
You could setup wvdial (run wvdialconf in a term) & create a launcher for wvdial in your panel--it will interface with pon/poff...Could be a simple answer....check it's man page out.

---

### Post by harty83 on 2006-11-12
I think I will just stick with pon/poff :-)

---

### Post by odin1965 on 2006-11-21
I use GnomePPP and it works well in both dapper and edgy. You can make it dock in the panel upon connection. One problem I had with it was that it would autodetect my modem but it would not let me activate the interface until it could detect a dial tone. I frigged with it for a while before I plugged the phone line in, then it let me use the connection. I thought I would be able to set up GnomePPP, then connect the phone line, but that doesn't work.

---

### Post by Coburn on 2006-11-25
The original question for this thread could also be asked at the moto4lin project forum at sourceforge.net.

[http://sourceforge.net/projects/moto4lin](http://sourceforge.net/projects/moto4lin)

The guys there are pretty helpful.

I assume /dev/ttyACM0 is a Motorola phone.

---

### Post by fragos on 2006-11-25
Networking is how you activate network connections.  wvdial is installed by default with Ubuntu but I don't see where you need to access anything other than Networking to setup dial up connections.  I've seen gnome-network-manager and wifi-radar interfere with each other preventing wireless connections to establish.  there may be a similar situation here.

---

### Post by nzgreen on 2006-11-27
Hi harty83.  I too am trying to get NetworkManager to initiate a dial-up connection.  Well, it is working, but as you have mentioned NM is not being notified that the connection is up.  Without an active connection I am unable to then start VPN connections which is kind of annoying.  I have both PPTP and OpenVPN connections setup with NM but I can only connect them when NM "knows" about an active connection.

This is the last piece of functionality I require from NM.  Then I can get rid of my scripts and use NM for all of my network connections ( well, expect ones with static ip addresses :-( )

To install network-manager-openvpn grab the .deb file from here:
[http://news.u32.net/](http://news.u32.net/)

HTH

---

### Post by Coburn on 2006-12-01
> **harty83 said:**
> I can't get gnome's built in dial up modem admin to work with my cell phone so I have to use a manually created peer file.  Is there a way to tell gnome-ppp to use a manually created peer file rather than create its own each time?

This is an excellent question.  I also would like a direct answer to it.

<info pppconfig> says that I need to do this to allow non-root users normal access to pppd.  But it assumes I know how.

I don't :-? 

If somebody would give a direct reply to this issue, we would also solve the problem you are having with network-admin.  

And many other users would then be able to set up a Bluetooth modem.

---

### Post by fragos on 2006-12-01
The answer to your question will be dependant on a number of factors including who your carrier is and which data plan you have.

---

### Post by Mach1US on 2006-12-14
I have Motorola v3 by verizon with EVDO modem to which i have subscribed.
This phone is being connected to my laptop by usb cable called by verion " Mobil office Kit " which comes with usb drivers for XP .
Verizon software disables BlueTooth data capability on that handset so my  question would be is there any way to use this phone as modem via usb cable ?:-k

---

### Post by fragos on 2006-12-14
I don't know that phone but if it supports web access it has what it needs to be used as a cellular modem.  I've used a serial cable with an LG phone as a modem for my Palm E2.  Verizon has a low speed data rate of 14.4K suitable for email that is paid for with voice minutes.  Higher speeds require a data plan as for 1X or EVDO.  I wouldn't be surprized if you could use the USB to phone cable with Linux.  Like all things Linux it's probably a matter of configuration and drivers.  I've set up TCP/IP connections trough my Linux box to access the Internet over my broadband cable.  That was over a USB connected Palm E2.

---

### Post by Mach1US on 2007-01-23
I have finally managed to set up my Motorola phone so i'v included all instructions in this HOW TO .
I can access my high speed conection via verizon evdo but if any body is interested in getting legal free dial up internet access  witch is suitable for e-mail and very slow internet access check this post and feel free to post your questions :

[http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo+motorola](http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo+motorola)

---

