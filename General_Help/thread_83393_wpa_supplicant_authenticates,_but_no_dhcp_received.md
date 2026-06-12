---
title: "wpa_supplicant authenticates, but no dhcp received"
date: 2005-10-28
forum: General Help
---

### Post by edwardog on 2005-10-28
I have a wpa-psk wireless network at home, running on a D-Link 
DI-524.  I'm writing this post from my girlfriend's ibook connected wirelessly, so there doesn't seem to be any connection problems with the router itself.

I installed wpa_supplicant and changed the /etc/wpa_supplicant.conf file to my setup.  I also changed /etc/default/wpasupplicant to my setup (I'm using a madwifi card).

I run 
```

$ sudo su
# ifconfig ath0 up
# /etc/init.d/wpasupplicant

```

I check to see the status of my wpa situation with wpa_cli and see that everything looks good and authenticated.

I check my router's dhcp table and see that my card's mac address has appeared and been assigned an ip already(?!).

I run
```

# dhclient ath0

```

and it times out without giving me an address.

What's going on, and how can I get dhclient to help assign me an address, gateway and dns server?

---

### Post by edwardog on 2005-10-29
I have no idea why it works now, but using the network-admin tool under System -> Administration and deactivating ath0, then activating it again have cured things.

Can someone comment on what network-admin is doing behind the scenes?

---

### Post by Doc.Caliban on 2005-10-29
I have the same router.  If you are using the latest firmware, 3.20, DHCP is broken with the Intel 2200BG.  (That's the case in Wondows anyway.)    If that's the card you have, you may have to roll back the firmware to get DHCP.

-Doc

---

### Post by edwardog on 2005-10-29
Actually, I had 3.02 installed, but upgraded to 3.20 only to see my DHCP and WPA2 fixed.  What was broken about DHCP for you?

---

### Post by lonetree on 2005-10-30
Hi Edwardog,

seems like you have the same problem as I have. I am using a D-link 724P+ and 624+ at 2 differnet location, but both side have the same SSID. 

I am trying to connect with my notebook with DWL-G650 wireless card.

I thought I had set the wrong parameter that things work this way, until I saw your post.

I too have to deactivate the ath0 and reactivate via network manager.

Have you found the solution to this already?

---

### Post by edwardog on 2005-10-30
Hey Lonetree,

I'm not sure about this, but I'm fairly certain that you need to have a unique ssid for each access points, otherwise your hardware will get confused when connecting to either one of them if there's an overlapping area where you can "see" both access points.

I haven't found out what the network manager applet is doing in this case, but in my case, it has worked (mind you, it takes more than 10 seconds to get a dhcp-assigned address which seems rather long).

However, as it's
a) Working
b) Encrypted the way I want it to be
I don't really care that much.

---

### Post by Doc.Caliban on 2005-10-30
[QUOTE=edwardog]Actually, I had 3.02 installed, but upgraded to 3.20 only to see my DHCP and WPA2 fixed.  What was broken about DHCP for you?[/QUOTE]

Hey, that's cool.  Maybe it's just Windows.  3.20 is known to break DHCP with the 2200 if you use WPA2.  That's with the 524 Rev. C.   The earlier Rev may not do it.

My "real" wifi card is an Atheros 5005 based NIC that I need to do the whole wrapper thing for.  In the mean time I'm using my old 2200 and things are working fine but I'm just running with WEP because I'm only a day or two into the install and I'm still having problems with more important things.  If I get them worked out, I'll be working on switching NICs and getting WPA2 working.

-Doc

---

### Post by edwardog on 2005-10-30
Maybe I'm just lucky: I've got a Rev. C working with DHCP and WPA2 (wpa_supplicant's logs confirm this).

The DHCP is kind of laggy, but it does work if I use the network manager application under Gnome.  (But it *doesn't* work if I just use dhclient, after authenticating with wpa_supplicant, which is the way it should work.)

What's bizarre is that the router will assign an authenticated wireless nic with a dhcp-allocated ip, but without the dhcp client asking for it.

However, since the upgrade, my girlfriend's iBook is having sporadic connection problems with the access point.  Weirdness.

---

### Post by NewbieNik on 2005-10-30
[QUOTE=edwardog]

I'm not sure about this, but I'm fairly certain that you need to have a unique ssid for each access points, otherwise your hardware will get confused when connecting to either one of them if there's an overlapping area where you can "see" both access points.
.[/QUOTE]


Ah, our lovely and mildly irrating wireless networking issues raise their ugly head again! Edwardog, you are spot on. The networks are not only identified by their essid but that is also tied in to the wireless access points hardware (MAC) address. Using two essid's the same will only confuse the user, not the hardware.
For an easy life name them seperately.

I had a major issue getting my D-Link DWL-AG650 PCMCIA card to work on an encrypted network so cheated in the end and put Smoothwall on a redundant PC and plugged the wireless router into the DMZ on that with WEP on in an open network.
Works a treat, but is probably causing huge amounts of global warming and drowned some bugs in the pacific isles...
Still if its not windows, its worth it!

---

### Post by lonetree on 2005-10-31
[QUOTE=edwardog]Hey Lonetree,

I'm not sure about this, but I'm fairly certain that you need to have a unique ssid for each access points, otherwise your hardware will get confused when connecting to either one of them if there's an overlapping area where you can "see" both access points.

I haven't found out what the network manager applet is doing in this case, but in my case, it has worked (mind you, it takes more than 10 seconds to get a dhcp-assigned address which seems rather long).

However, as it's
a) Working
b) Encrypted the way I want it to be
I don't really care that much.[/QUOTE]


Hi Edward,

first, I have to clarify that both my routers are not within the same vincinity, one is at home and the other in the office. So there won't be any overlapping. 

For my case, I always have to type "sudo wpa_supplicant -B -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w -dd" in terminal and start network manager to get connected to the wireless network. Although this isn't much of a problem, but having to do this everytime is quite troublesome, and I have to mount all my network drive manually.

Really hope that someone who is facing the same problem could help.

Thanks in advance.

regards,

---

### Post by edwardog on 2005-11-01
[QUOTE=lonetree]Hi Edward,

first, I have to clarify that both my routers are not within the same vincinity, one is at home and the other in the office. So there won't be any overlapping. 

For my case, I always have to type "sudo wpa_supplicant -B -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w -dd" in terminal and start network manager to get connected to the wireless network. Although this isn't much of a problem, but having to do this everytime is quite troublesome, and I have to mount all my network drive manually.

Really hope that someone who is facing the same problem could help.

Thanks in advance.

regards,[/QUOTE]

After installing wpa_supplicant through apt-get, a service file is set up for you at /etc/init.d/wpasupplicant

I have a few lines of that that look like
```

...

DAEMON=/usr/sbin/wpa_supplicant
PIDFILE="/var/run/wpasupplicant.pid"
CONFIG="/etc/wpa_supplicant.conf"
PNAME="wpa_supplicant"

# insane defaults
OPTIONS="-Bw" # daemonize and wait for interface
ENABLED=0

...

```

Once you've edited that, you can start the service from the console with ```
sudo /etc/init.d/wpasupplicant start
```.  If your wpa_supplicant.conf is all set up properly and your wireless interface is active, everything should be taken care of for you.

(Mind you, I always have to activate / deactivate / activate my wireless interface anyway for some unknown reason, but at least it works.)

---

### Post by lonetree on 2005-11-19
Some updates here, just tested with an linksys AP, wpa works without having to deactivate and re-activate to make wpa works. The system just gets an IP address from the dhcp at start up.

regards,

P/S: how is your side with the dlink, edward? I still have no luck for my dlink yet. Have to run the wpa script after loggin into the system.

---

### Post by edwardog on 2005-11-19
Since the dlink sits at my parents' place 2 hours away, I don't get to use it much.

Lonetree: How come you have to run the wpa script manually?  When I installed it, wpasupplicant ran as a service.

---

### Post by lonetree on 2005-12-04
[QUOTE=edwardog]Since the dlink sits at my parents' place 2 hours away, I don't get to use it much.

Lonetree: How come you have to run the wpa script manually?  When I installed it, wpasupplicant ran as a service.[/QUOTE]

Hi Edward, sorry to reply only now. If I don't run the wpa script and reactivate the network manager together, I will never get an IP address from the router. 

One bad news, these few days, I dun even get any IP assigned at all. As I can see, I actually got an IP  address assigned and it just break off immediately after it. :-(

---

