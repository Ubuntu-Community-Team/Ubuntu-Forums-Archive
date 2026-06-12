---
title: "NetworkManager's strange behaviour"
date: 2006-12-14
forum: General Help
---

### Post by lfys on 2006-12-14
After reading about WPA and Ubuntu I came to the conclusion that the allegedly fantastic  NetworkManager behaves a little strange on my computer (Ubuntu 6.06)

It should look somewhat like this:

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]
([http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png](http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png))

but actually looks like this:

[IMG]http://schoolweb.rago.be/kta/mechelen/paramedisch%20instituut/temp/nm_applet.jpg[/IMG]
([http://schoolweb.rago.be/kta/mechelen/paramedisch%20instituut/temp/nm_applet.jpg](http://schoolweb.rago.be/kta/mechelen/paramedisch%20instituut/temp/nm_applet.jpg))

No extra possibilities for me.
How is that possible?

---

### Post by mcduck on 2006-12-14
it has two menus, depending on which mouse button you use to click it. Also the icon changes for no connection/wired connection/wireless connection. Try left-click.. ;)

---

### Post by lfys on 2006-12-14
left click reveals a greyed out line that tells me there 's no network devices configured.

---

### Post by mcduck on 2006-12-14
Ok. The way I got Network Manager working was removing all configurations from Gnome's Network Settings, logging out and back again. After that Network Manager recognized my interfaces. You could try that.

---

### Post by Patrick-Ruff on 2006-12-14
could this possibly be a problem similiar to mine? I found that network settings wasn't launching with GKSUDO, still isn't entirely, it's realyl annoying, when I doubel click on the panel icon it doesn't automatically launch with gksudo, therefore, I have no access to any network devices.

---

### Post by lfys on 2006-12-14
```
"... removing all configurations from Gnome's Network Settings"
```

Where can I find those?

The only place I know of that contains the information to access my wireless network (which by the way works without any problem) is /etc/network/interfaces.

---

### Post by mcduck on 2006-12-14
> **lfys said:**
> ```
"... removing all configurations from Gnome's Network Settings"
```

Where can I find those?

The only place I know of that contains the information to access my wireless network (which by the way works without any problem) is /etc/network/interfaces.

I mean all settings you have made with Gnome's Network Settings tool (System/Administartion/Networking)

---

### Post by lfys on 2006-12-15
Just to make sure we are speaking about the same thing ...

Notice that I have 2 icons in my top panel that indicate network traffic.

[IMG]http://schoolweb.rago.be/kta/mechelen/paramedisch%20instituut/temp/nm_applet12.jpg[/IMG]

The right one works only with ehernet connections (cable is not plugged in).

The left one brings about a window like this one:

[IMG]http://www.opensolaris.org/os/project/nwam/stateoftheart/ubuntu/connection-properties-general.png[/IMG]

With that I can choose between wlan0 and Io. Then I can proceed to something like this: 

[IMG]http://www.linuxfrench.net/IMG/png/network-ubuntu-hoary1.png[/IMG]

Then I can choose whatever interface I want and configure it.
(No wpa with the wireless connection though)

I mean my wireless works fine but I would like NetworkManager let me choose easily between wireless networks AND allow me to select WPA security, which, as far as I understand it from what I read, it should do both.

---

### Post by mcduck on 2006-12-15
The way I've understood Network Manager is that it's not a tool to be used together with the Network Settings (the other tool you have, also available in System/Administration/Networking) but *instead* of that one. So to get Network Manager working you must let Network Manager configure your network instead of doing it yourself with some other tools.

And my own experiences seem to support this.

When I installed Network Manager I had a working connection with several profiles in Network Settings. Network Manager told me that there are no network interfaces, just like it's telling to you now. Then I destroyed all my network configurations, effectively *killing* my network connection, and rebooted. Now Network Manager recognized both my wired and wireless interfaces and handled all connections. If I go to Gnome's network settings it's telling me that I have no configured network interfaces.

So, Network Manager allows you to choose between different networks, allows using WPA, and even does automatic switching between networks. But only when it's the only app handling your networking.

[IMG]http://www.elisanet.fi/pontus.schonberg/random/networksettings.png[/IMG]
[Network Settings]("http://www.elisanet.fi/pontus.schonberg/random/networksettings.png")

[IMG]http://www.elisanet.fi/pontus.schonberg/random/nmapplet.png[/IMG]
[Network Manager]("http://www.elisanet.fi/pontus.schonberg/random/nmapplet.png")

---

### Post by lfys on 2006-12-15
Thank you for the clear explanation, mcduck.

I'll try it this weekend and keep you informed.

---

### Post by lfys on 2006-12-18
Mmm. Didn't work yet.

Maybe I missed something and did not stop all services running? Or I didn't remove every configuration?

Should I uninstall something?
Remove /ect/network/interfaces ?
...

---

### Post by NeoChaosX on 2006-12-18
The easiest way to do it is just clear your /etc/network/interfaces file so it looks like this:
```
auto lo
iface lo inet loopback
```
Then, just restart your computer and NetworkManager should start picking up wireless networks

---

### Post by lfys on 2006-12-19
Yes.
Now it does (almost) what you've told.

It shows me the unprotected wireless network of our neighbours :) 
However I can't seem to establish a connection.

Also it fails to connect to my own (protected) network. And WPA is not listed in he security options.

---

