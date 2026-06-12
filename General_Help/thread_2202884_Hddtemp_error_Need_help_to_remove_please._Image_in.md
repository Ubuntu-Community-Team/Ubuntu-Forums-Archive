---
title: "Hddtemp error Need help to remove please. Image included"
date: 2014-01-31
forum: General Help
---

### Post by ManyBeers on 2014-01-31
Xubuntu 12.04 xfce desktop on a Gateway netbook. Anyways as the image shows the instant I add sensor 
plugin to the panel the error pops up , also if I leave the sensor plugin on the panel and restart the error is displayed
once again. If I remove sensor plugin from the panel the message is gone. I had installed hddtemp but it has since 
been removed. So somehow the sensor plugin seems to be the source of the error message. Any help is appreciated.
Thanks.

---

### Post by Impavidus on 2014-01-31
The xfce sensors plugin relies on hddtemp to find the temperature of your HDD. With hddtemp not installed, it won't work. Either install hddtemp or configure the plugin not to show the temperature of your HDD. Or remove the plugin from your panel.

---

### Post by ManyBeers on 2014-01-31
> **Impavidus said:**
> The xfce sensors plugin relies on hddtemp to find the temperature of your HDD. With hddtemp not installed, it won't work. Either install hddtemp or configure the plugin not to show the temperature of your HDD. Or remove the plugin from your panel.

I don't have the plugin configured to show hd temps. The only reason I use it is to keep an eye on my cpu temp. There must be a file or 
something I can edit to stop sensors from trying to start or find hddtemp. Where is it?

---

### Post by deadflowr on 2014-01-31
I know nothing about this panel addon/plugin, but does it happen to launch at start up.
Maybe look in the start-up applications program(?).

---

### Post by ManyBeers on 2014-02-01
Will this help? I think I need to change. the Suppress hdd message=false to true. How do I do that?

---

