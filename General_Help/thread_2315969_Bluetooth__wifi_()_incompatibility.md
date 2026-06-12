---
title: "Bluetooth / wifi (?) incompatibility"
date: 2016-03-04
forum: General Help
---

### Post by nickTaylor1181 on 2016-03-04
Hi all

I am having serious difficulties getting bluetooth audio to work.

Two different laptops (one 14.04, the other 15.04), both showing the same symptoms with two different devices. Windows (dual boot on the same machine) works fine. Android on a different device works fine.

What happens is that when when bluetooth is running and a youtube video is also running, its splutters and stops and starts, then if/when it starts working again, there's a lag of several seconds. 

I've completely reinstalled entire operating systems several times.


Any help much appreciated.




Nick

---

### Post by nickTaylor1181 on 2016-03-06
It looks like there's a basic clash between wifi and bluetooth.

At the moment it won't load any website at all if bluetooth is running... until I physically switch it off, and then the web connection starts working again.

I don't know what diagnostic stuff to provide with this.

---

### Post by nickTaylor1181 on 2016-03-10
It seems this bug is 8 years old. FFS.

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/219057](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/219057)

Anybody had any experience with actually getting this to work?

---

### Post by nickTaylor1181 on 2016-03-21
Right - well I finally 

a) changed from Ubuntu to Mint (which basically is Ubuntu, so no change).

b) used an external USB dongle, with Blueman - which (touch wood) seems to have fixed it... so long as the original internal bluetooth adaptor is disabled.

...

This whole experience has severely shaken my faith in Ubuntu - I thought it was getting better and better... and if something goes wrong, there's  a community to help you out.

Not so apparently.

---

### Post by nickTaylor1181 on 2016-03-21
Right - well I finally 

a) changed from Ubuntu to Mint (which basically is Ubuntu, so no change).

b) used an external USB dongle, with Blueman - which (touch wood) seems to have fixed it... so long as the original internal bluetooth adaptor is disabled.

---

### Post by jeremy31 on 2016-03-21
I don't look at the general forums often, but some wifi drivers have a btcoex parameter and changing it from the default setting sometimes helps

You can find your wifi driver with ```
lspci -nnk | grep -iA2 net
```

It will show ethernet and wireless and importantly Kernel driver in Use:
Once you know the driver you can use ```
modinfo -p
``` followed by the module name to see what parameters are available

The iwlwifi module shows
```
bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
```

and ath9k shows
```
btcoex_enable:Enable wifi-BT coexistence (int)
```

---

### Post by nickTaylor1181 on 2016-03-21
Hiya - thanks for the reply.

I'll make a note of these and keep them for diagnostics if I need to try to fix this again... but as it is (right now) I do (albeit via a bodgy workaround) have a working system, and I'm loathe to touch anything that might break it.  It has taken literally months of searching and trialling/erroring to get to this point. 

I did tinker with [COLOR=#000000]iwlwifi settings - but didn't really know what I was doing, so didn't see a whole lot of change.


Thanks tho - appreciated.[/COLOR]

---

