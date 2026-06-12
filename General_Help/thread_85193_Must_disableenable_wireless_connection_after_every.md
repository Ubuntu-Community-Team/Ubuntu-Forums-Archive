---
title: "Must disable/enable wireless connection after every boot"
date: 2005-11-02
forum: General Help
---

### Post by Doc.Caliban on 2005-11-02
I've found that while the wireless connection establishes itself with the AP after boot, I don't have any network connectivity.  If I disable and then re enable the connection, everything works again.  This happens with both DHCP and static IP configurations.

Also, what is the linux command to display current IP addresses for an adapter?  (Like IPCONFIG in Windows)


-Doc

---

### Post by RAOF on 2005-11-02
Can't help with the first, but ifconfig is the command you're after.

---

### Post by Doc.Caliban on 2005-11-02
[QUOTE=RAOF]Can't help with the first, but ifconfig is the command you're after.[/QUOTE]


I appreciate that.  Tough to troubleshoot networking issues without that info!

-Doc

---

### Post by Doc.Caliban on 2005-11-02
(bump)

This is causing several problems for me and I'm still unable to find a resolution.

Regards,

-Doc

---

### Post by MarcDM on 2005-11-03
[QUOTE=Doc.Caliban]If I disable and then re enable the connection, everything works again.  This happens with both DHCP and static IP configurations.[/QUOTE]

This happens due to what I believe is a bug (haven't filed it though).

In the file /etc/network/interfaces  there's a section that says :
```

mapping hotplug
        script grep
        map eth0

```
at the top. To make the wireless connection come up automatically, add the name of the device to the map line.

On one laptop, I changed the line to read :
```
map eth0 ath0
```

[QUOTE=Doc.Caliban]Also, what is the linux command to display current IP addresses for an adapter?  (Like IPCONFIG in Windows)
[/QUOTE]
the program clasically used to display/configure network interfaces is ifconfig usually located at /sbin/ifconfig

However the ip program (/sbin/ip), from the iproute2 project, also achieves the same purposes with some added flexibility.

quick tutorial :
 - [LIST]
[*]ip addr ls  # lists ip addresses on all devices
[*]ip addr ls dev eth0 # give addresses for eth0
[*]ip addr help # help on the address functions of the ip program
[*]ip help # help on the various functions of the ip program
[/LIST]
 
Hope this helps.

Marc DM

ps. the items in that list are in the format *command* # *comment*

---

### Post by ecobuntu on 2005-11-03
This works for me.../etc/network/interfaces

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid any

---

