---
title: "Where can I get hotplug and is it better than usbmgr?"
date: 2007-03-11
forum: General Help
---

### Post by dryder on 2007-03-11
Hi,

I have a Microtek 5800 scanner. The SANE website recognizes it as a 3800 using the {idVendor}=="05da" and {idProduct}=="30d4" using lsusb.

To help me tring to get it to work I instal usbmgr but noted it said:
"For wider and modern support of plugable devices you may want to use hotplug." Is it really better?

Can anybody tell me where I can obtain 'hotplug' - it's not in Synaptic Packages and I can't find a download site however much sourceforge et al talk about it.

Many thanks,

David

---

### Post by x64Jimbo on 2007-03-11
Hotplug is built into most modern linux distros. What software have you tried to use with it, and how do you know it's not working already?

---

### Post by dryder on 2007-03-11
> how do you know it's not working already?
An excellent question - I don't know it isn't - it never occurred to ma. The statement > you may want to use hotplug in synaptic under usbmgr implies it, so I assumed it.

> What software have you tried to use with it
I have only been trying to get my scanner recognised using XSane and Kooka. It shows up in lsusb, as previously mentioned, and as SANE identifies it there is a very good chance it uses the same chip - in which case I should get some response from it, good or bad, instead of just sitting there.

Using lsusb I note on each boot the Bus and Device number change, which surprises me - I assume the sequence of bus interrogation is not 'fixed'.

David

---

