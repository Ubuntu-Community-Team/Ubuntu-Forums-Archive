---
title: "Ubuntu 20.04 server 64bit for Raspberry Pi 4: how to enable wifi support, from CLI?"
date: 2020-05-01
forum: General Help
---

### Post by esbeeb on 2020-05-01
Hello,
I have a Raspberry Pi 4.  I can get wifi (both 2.4GHz and 5GHz) working from the CLI quite easily in Raspbian 32bit, but it's very hard to do in Ubuntu 20.04.  Netplan is something new to me, and seems buggy.

After a fresh imaging of a MicroSD card, there will be a tempting  "network-config" file in the partition with the boot-related stuff  (labelled "system-boot").  Either working from the wifi example provided  in that file, **or** putting the paragraph below into this "network-config" file before first boot  doesn't work either.  Yes, I substituted in my own password, and SSID.
```

network:
  version: 2
  renderer: networkd
  wifis:
    wlan0:
      dhcp4: true
      optional: true
      access-points:
        "SSID name goes here":
          password: "password goes here"
```

So how to enable wifi from the CLI?

I've come up with a cumbersome workaround: before that first boot, have the RPi4 connected by an ethernet cable.  Netplan will use DHCP to get into your LAN.  Once you can SSH in, then install "network-manager".  Once network-manager is installed, you can now connect to 2.4GHz wifi only (**not 5GHz**), with commands like the following:

```

sudo nmcli r wifi on
sudo nmcli d wifi connect "2.4GHz SSID name" password "my wifi password"

```

Is there a better way, which avoids the need for an ethernet cable first (to install nmcli, which is not included in a default install)?

---

### Post by waveform on 2020-05-01
> **esbeeb said:**
> Hello,
I have a Raspberry Pi 4.  I can get wifi (both 2.4GHz and 5GHz) working from the CLI quite easily in Raspbian 32bit, but it's very hard to do in Ubuntu 20.04.  Netplan is something new to me, and seems buggy.

After a fresh imaging of a MicroSD card, there will be a tempting  "network-config" file in the partition with the boot-related stuff  (labelled "system-boot").  Either working from the wifi example provided  in that file, **or** putting the paragraph below into this "network-config" file before first boot  doesn't work either.  Yes, I substituted in my own password, and SSID.

There's definitely some bugs to work out yet! The "network-config" file on the boot partition does have one relevant issue: its contents are copied correctly to the netplan configuration, and rendered correctly, but for some reason they don't apply on first boot (see [LP: #1870346]("https://bugs.launchpad.net/ubuntu/+source/cloud-init/+bug/1870346") - we're still working on this; not sure if it's cloud-init or netplan but the latter is currently looking likely).

> **esbeeb said:**
> So how to enable wifi from the CLI?

I've come up with a cumbersome workaround: before that first boot, have the RPi4 connected by an ethernet cable.  Netplan will use DHCP to get into your LAN.  Once you can SSH in, then install "network-manager".  Once network-manager is installed, you can now connect to 2.4GHz wifi only (**not 5GHz**), with commands like the following:

```

sudo nmcli r wifi on
sudo nmcli d wifi connect "2.4GHz SSID name" password "my wifi password"

```

Is there a better way, which avoids the need for an ethernet cable first (to install nmcli, which is not included in a default install)?

To enable wifi on first-boot at the moment, here's another work-around. Stuff the configuration in "network-config" as usual, then add the following to "user-data":

```

runcmd:
- reboot

```

That only runs on the first boot (it won't go into a perpetual boot cycle), but causes it to reboot after having copied the network-config to netplan. On the second boot, wifi *should* work (assuming "network-config" is correct).

---

