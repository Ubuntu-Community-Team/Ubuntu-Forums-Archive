---
title: "network-manager nm-applet bugs"
date: 2008-02-28
forum: General Help
---

### Post by komputes on 2008-02-28
Where does nm-applet keep list of known (connected) wireless networks?

I have a few problems that I have posted on launchpad, perhaps someone on the forums can give me some insight on what the issue might be.

For some reason, nm-applet keeps spinning, when I connect to a cabled network. There is no problem with the network, and I can usually get an IP address through dhclient. So here are the bugs:
 1) Network manager is not able to grab an IP when dhclient is able to, quite quickly. (is there a way to put dhclient within nm-applet, so that it's run when a cable connects.)


 2) After using dhclient, the IP address shown in ifconfig is correct, but the one in nm-applet is 0.0.0.0
Is there a problem with nmapplet grabbing/refreshing the current IP address?


3) Each time you connect to a wireless access point, a line is added to a configuration file (which I am currently trying to find, help is appreciated), stating the name of that access point. If you connect to 3 access points you should have 3 cascading access point in this nm config file. Yet, let's say that we need to remove one of those access points because it is interfering with another access point (with a similar name). nm-applet does not give a graphical option to the user, to view this list of AP's that have been associated in the past, so that the user may edit the configuration or delete it from the list all together.
 In easy-speak: You can connect to an access point, but you can't disconnect from one, short of connecting to another access point or disabling wireless.

Launchpad Bugs: 
196710                    [nm-applet DHCP request takes a lot of time, and gives no address]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/196710")                                      
196705                    [nm-applet does not show list of _PAST_CONNECTED_ access points.]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/196705")

---

### Post by komputes on 2008-02-28
Solution to #3 - Wireless Preferred Networks: Ok, so I went the long complicated way and found the directory which contains the information of the "auto-connect" access points which have been associated with this computer in the past.

The dir is:
~/.gconf/system/networking/wireless/networks/

One directory (named after the SSID of the AP) is created for every access point which the computer has been associated with. within that directory is a %gconf.xml file which contains information pertaining to the Access Point. What I don't understand is how that configuration file talks to the keyring to get the password/key for the access point. I have tested my theory by removing one directory, and it works perfectly. After that it did not reconnect to that AP automatically.

---

