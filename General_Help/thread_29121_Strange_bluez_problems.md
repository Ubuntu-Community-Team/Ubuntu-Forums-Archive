---
title: "Strange bluez problems"
date: 2005-04-23
forum: General Help
---

### Post by ltmon on 2005-04-23
EDIT: Solved.  It turned out to be a syntax error in hcid.conf.  You can track these down by stopping bluetooth, and then running (as root) "hcid -n".  This will give you basic output your config file.

Cheers,

L.

-------------

Hi All,

I have installed bluez to use to transfer files to and from my phone.

It's working fine apart from the fact that I can't configure it at all.  I modify the file /etc/bluetooth/hcid.conf, but none of the modifications are present in the hcid when it is restarted.

For example, in hcid.conf I have the line in my device section:

# Local device class
        class 0xff0100;

But when I probe the device with hciconfig -a, the class is reported as:

Class: 0x000000

The same occurs with the bluetooth device name - I have set it to my host name, but it appears as "Mavin" for some reason. 

All I can think of is that the hcid is not using the default config file, but start hcid with 'hcid -f /etc/bluetooth/hcid.conf' makes no difference.

Any ideas what could be causing this?

Thanks.

L.

---

