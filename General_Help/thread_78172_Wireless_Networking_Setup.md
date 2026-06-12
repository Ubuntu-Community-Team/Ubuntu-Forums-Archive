---
title: "Wireless Networking Setup"
date: 2005-10-17
forum: General Help
---

### Post by fogNL on 2005-10-17
I'm not sure if i'm missing something here or not, hopefully someone can tell me an automated way...

I have a fresh install of Kubuntu breezy.  My wireless card works fine (ipw2200 led=1).  What I want is for when I log into KDE, that my Wireless card automatically connects to my network (we'll call the ssid "foobar") and then. broadcast for dhcp.  I'm using KWifimanager, and i went into the settings and setup Config 1 with my home network (which i almost always use).  I entered in the ssid, and told it to load Config 1 automatically on startup for eth0.  However, whenever i log into KDE, KWiFimanager opens, but it doesn't do anything automatically.  What I end up doing is having to go into kwifimanager settings again and click "Activate" next to the "Configuration to Load" line.  Which connects me to my network but doesn't give me an ip.  Then I go over to konsole and execute "sudo dhclient eth0" and everything is fine.
I know this isn't much of an issue, I would just like to find a way for this to happen automatically, and I would assume that clicking on the option in kwifimanager to "load preset on startup" should give me this effect, but it doesn't.  I even created a script for "Execute script on connect" that would run dhclient for me, but that doesn't work either.

Any suggestions?

---

### Post by paxmark on 2005-10-18
That has been my life in hoary with a dlink 802.11b that is supported.

After messing around with /etc/network/interface - it popped up one time perfect when I started up.  For awhile I only had to sudo dhclient wlan0.

But I am back now to kwifimanager, activate, and then still sudo dhclient wlan0.  I will wait some more before going to breezy.

peace,  mark

---

### Post by rsankuratri on 2005-10-18
Edit your /etc/network/interfaces file and see that you have the following:
###################################
# The primary network interface
auto wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid YOUR_ESSID_GOES_HERE
wireless-key YOUR_WIRELESS_KEY HERE
###################################

Hope this helps  ;)

---

### Post by Nathaniel on 2005-10-19
Thanks for saving me from making a new topic, I have the exact same problem :)

I tried the last suggestion, and am rebooting as we speak. I would, however, like to know how I add several networks, so as to let the computer connect to whatever network in the list that's available on boot. Since I move frequently between my home and my school, this would save me quite some time :)

---

### Post by lou_sid on 2005-11-02
while the whole "manually clicking activate" deal is still annoying, you can at least avoid the extra dhclient step by adding:

sudo dhclient wlan0

to the "execute script on connect" field

---

### Post by theclaw on 2005-11-02
I found KWifimanager to be a pile of shit. I have an ipw2100 built in card. KWifimanger would not let me connect to my router. I got wifi-radar with apt and that works. I set up the connection and I get connected on boot. I didn't set anything extra it just worked. 

edit: So, try wifi-radar, see if that helps.

---

### Post by Copter on 2005-11-06
hi!

ive also found out that _all_ gui network programs are piece of crap. only thing that helped me was writting this small iwconfig script:

```
#! /bin/sh
ifdown wlan0
sleep 1
echo 'Setting essid'
iwconfig wlan0 essid "nitro"
echo 'Setting channel'
iwconfig wlan0 channel 6
echo 'Setting mode'
iwconfig wlan0 mode Managed
echo 'Setting ap'
iwconfig wlan0 ap 00:0F:3D:67:19:92
echo 'Setting rate'
iwconfig wlan0 rate auto
echo 'Setting key s'
iwconfig wlan0 key s:xsxsxsxsxsxsx
echo 'Setting key open'
iwconfig wlan0 key open
echo 'Setting txpower'
iwconfig wlan0 txpower 20
echo 'Setting sens'
iwconfig wlan0 sens 91
echo 'Setting power management'
iwconfig wlan0 power all
echo 'iwconfig wlan0 commit'
iwconfig wlan0 commit
sleep 1
ifup wlan0
echo 'Setting route'
route add default gw 192.168.0.1

```
now if i want to activate wifi, or something bad is happening to my connection i run this script in root mode (sudo script_name.sh). some values above has been taken using iwlist program.

btw. my card : D-Link DWL-650+ (CardBus) - working ok

copter :]

---

### Post by PiratesOverNinjas on 2006-03-29
[QUOTE=Copter]hi!

ive also found out that _all_ gui network programs are piece of crap. only thing that helped me was writting this small iwconfig script:

```
#! /bin/sh
ifdown wlan0
sleep 1
echo 'Setting essid'
iwconfig wlan0 essid "nitro"
echo 'Setting channel'
iwconfig wlan0 channel 6
echo 'Setting mode'
iwconfig wlan0 mode Managed
echo 'Setting ap'
iwconfig wlan0 ap 00:0F:3D:67:19:92
echo 'Setting rate'
iwconfig wlan0 rate auto
echo 'Setting key s'
iwconfig wlan0 key s:xsxsxsxsxsxsx
echo 'Setting key open'
iwconfig wlan0 key open
echo 'Setting txpower'
iwconfig wlan0 txpower 20
echo 'Setting sens'
iwconfig wlan0 sens 91
echo 'Setting power management'
iwconfig wlan0 power all
echo 'iwconfig wlan0 commit'
iwconfig wlan0 commit
sleep 1
ifup wlan0
echo 'Setting route'
route add default gw 192.168.0.1

```
now if i want to activate wifi, or something bad is happening to my connection i run this script in root mode (sudo script_name.sh). some values above has been taken using iwlist program.

btw. my card : D-Link DWL-650+ (CardBus) - working ok

copter :][/QUOTE]
Seems like a good idea, but one question? Is 192.168.0.1 the ip address of your wireless gateway?

---

### Post by louiech21 on 2007-07-17
I am running Ubuntu 7.04 on my HP Pavilion ze2000 and I can't seem to do anything to get my wireless card detected.  What should I do?  I tried the scripts on this reply to thread and I closely watched the commands, I was unable to have my internal wireless card or my external Verizon PCMCIA wireless 802.11 / CDMA.  I have the windows setup software for the Verizon card installed in wine and ready to run in Ubuntu but I can't get any type of wireless from either of the two wireless cards.  Any suggestions?  I am open to anything to get my wireless working either my 802.11g wireless or my PCMCIA Card either way I would just love to be able to go wireless again.  Please help!  I'm stuck at the desk again :(

---

### Post by louiech21 on 2007-07-19
Nevermind my wireless works awsome now!
:popcorn:

---

