---
title: "iw support on reboot"
date: 2017-04-22
forum: General Help
---

### Post by justina2 on 2017-04-22
I have a need for the following:
The ability to have a station, and an __ap virtual interface on my install. This is a lab I am building, and I need the options to connect the lab to a guest wifi while being connected to it directly.

I have the commands worked out, 

Delete the normal wifi interface
 - iw dev wlp3s0 del

Create my 2 new virtual interfaces
 - iw phy phy0 interface add Vwlan0 type station
 - iw phy phy0 interface add Vwlan1 type __ap

This works GREAT, my 2 virtual interfaces come up, and I am able to launch hostapd on the __ap, and able to use station to connect to a wifi.

The challenge that I have is how do I allow this persist on reboot.
I need to delete the wlp3s0 interface, and create the 2 virtual interfaces. 

I have tried using a udev rule:
ACTION=="add" , SUBSYSTEM=="ieeee80211", KERNEL== "phy0", RUN+="/sbin/iw phy %k interface add Vwaln0 type station", RUN+="/sbin/iw phy %k interface add Vwlan1 type __ap"

This did not work, so am striking out on what the appropriate approach would be.

--J

---

### Post by yetimon_64 on 2017-04-22
> **justina2 said:**
> ...
Delete the normal wifi interface
 - iw dev wlp3s0 del

Create my 2 new virtual interfaces
 - iw phy phy0 interface add Vwlan0 type station
 - iw phy phy0 interface add Vwlan1 type __ap

...

[U][I] Do you run those 3 commands as root normally (with sudo) or as you have typed them above ?
[/I][/U]
IF they do run as root (with sudo usage) you can add them to the file /etc/rc.local to have them executed at each start up.

To edit the /etc/rc.local file ...
```
sudo -H gedit /etc/rc.local
```

Then add in the commands so the file looks like ...

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iw dev wlp3s0 del
iw phy phy0 interface add Vwlan0 type station
iw phy phy0 interface add Vwlan1 type __ap

exit 0
```
Note: the /etc/rc.local file runs as root at startup and as such you don't need to use the sudo command before any commands being run from there.

Save the file and test with a reboot.

---

### Post by justina2 on 2017-04-23
This appears it may have worked, will respond if this does not.

I was worried about ensuring that the interfaces would be built prior to hostapd being launched.

Thanks.

-J

---

