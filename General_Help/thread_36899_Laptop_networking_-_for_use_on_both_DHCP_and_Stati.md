---
title: "Laptop networking - for use on both DHCP and Static IP networks"
date: 2005-05-25
forum: General Help
---

### Post by Sleeper Service on 2005-05-25
I've now got Ubuntu 5.04 on my laptop as well as desktop (hoorah!).  But I've got some networking dilemmas:

I'm sometimes connected to me home network (Linux, DHCP) and sometimes to the work network (Linux, Static IP only).

Is there a way I can have a couple of ethernet settings which are started manually once I've logged in?  Or perhaps an auto-detect option that works out which network I'm on and choose from two different settings?

One of the complications is that I need to work well enough to mount directories (using nfs) on other machines on both networks.

And another thing - I occassionally use the laptop with no network connection at all - in which case, I have to wait for ages during start up while Ubuntu tries to find its network time server.  Can this check also be switched of and done manually.

Cheers.
SS

---

### Post by dave9191 on 2005-05-25
I'm in the same kind of situation as you. What I did was edited the network config file not to start any network connnections and I wrote a shell script for each network I connect to. Then I created icons for each script and I can just click on the icon corresponding to the network I wan to connect to. You can find example scripts here [http://ubuntuforums.org/showthread.php?t=28869](http://ubuntuforums.org/showthread.php?t=28869) post 7. Im going to be remaking them and making a howto in a couple of weeks time. Hope this helps. 

Dave

---

### Post by Sleeper Service on 2005-05-25
That's really helpful - thanks.  I'll feedback here (or there) once I've got it working.

---

### Post by Sleeper Service on 2005-05-31
[quote=dave9191]I'm in the same kind of situation as you. What I did was edited the network config file not to start any network connnections[/quote]Could I ask how you did this?

> and I wrote a shell script for each network I connect to.I've had a look at your wi-fi scripts, but I can't see what command I'd need to set networking to DHCP or Static IP?

---

### Post by dave9191 on 2005-05-31
This is my /etc/network/interface

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
#iface eth0 inet dhcp 

I commened out the lines which start network conections like ifcae eth0 inet dhcp

And to request dhcp you use the dhclient command. To set a static address you use ifconfig.

---

