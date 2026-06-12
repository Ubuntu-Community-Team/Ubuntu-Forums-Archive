---
title: "how to blacklist conflicting wireless drivers?"
date: 2012-12-21
forum: General Help
---

### Post by lightsaberlesbian on 2012-12-21
I'm currently running Kubuntu 12.10 and I think I have been experiencing wireless issues due to conflicting wireless drivers being loaded.  I have a g7-1070us and I believe my wireless driver is the broadcomm BCM-4313.  I've read that I should blacklist all other drivers besides the open driver, brcmmac i think is the name? but i'm not sure how to, or which ones to blacklist.

---

### Post by bkratz on 2012-12-21
> **lightsaberlesbian said:**
> I'm currently running Kubuntu 12.10 and I think I have been experiencing wireless issues due to conflicting wireless drivers being loaded.  I have a g7-1070us and I believe my wireless driver is the broadcomm BCM-4313.  I've read that I should blacklist all other drivers besides the open driver, brcmmac i think is the name? but i'm not sure how to, or which ones to blacklist.

Most people have had good luck with the sta driver rather than brcmmac? See this post

[http://ubuntuforums.org/showpost.php?p=12372044&postcount=4](http://ubuntuforums.org/showpost.php?p=12372044&postcount=4)

---

### Post by lightsaberlesbian on 2012-12-21
thanks.  will I not have to blacklist the other drivers? e.g. bcrmsmac, bcrms, etc.?

i'm assuming it might be something similar to > blacklist MODULE_NAME in /etc/modprobe.d/blacklist.conf and inorder to load the module add it in /etc/modules. So if you would like to use say wl you would add

blacklist brcmsmac
blacklist bcma
blacklist ssb
blacklist b43

---

### Post by bkratz on 2012-12-21
> **lightsaberlesbian said:**
> thanks.  will I not have to blacklist the other drivers? e.g. bcrmsmac, bcrms, etc.?

i'm assuming it might be something similar to



I believe that the STA driver automatically blacklists the others, but you might keep your list just in case!

---

### Post by lightsaberlesbian on 2012-12-21
Thanks!  Is there any way to determine which drivers are loaded so that I can doublecheck?

---

### Post by bkratz on 2012-12-21
> **lightsaberlesbian said:**
> Thanks!  Is there any way to determine which drivers are loaded so that I can doublecheck?

 [COLOR="Red"]sudo lshw -C network[/COLOR]
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: [COLOR="Blue"]driver=b43-pci-bridge[/COLOR] latency=0
       resources: irq:18 memory:d0200000-d0203fff''



If you do the command in red above *wait a couple of seconds for it to show up" You should see something like shown above but the blue part will say "wl" rather than what is in the sample above.

You could also do an lsmod to show the modules loaded.

---

### Post by lightsaberlesbian on 2012-12-21
Sick.  Just like you said.

---

### Post by bkratz on 2012-12-21
> **lightsaberlesbian said:**
> Sick.  Just like you said.

Does this mean you are running now?

---

### Post by lightsaberlesbian on 2012-12-22
I was always running.  I just kept getting disconnected or experienced difficulty in connecting to networks at times.  I'm definitely not getting disconnected.  I haven't had trouble connecting to the wireless today but sometimes that's contingent on the wireless signal during the day (it kinda varies day to day).  Usually when that happens I have to boot into Windows 7 to secure a connection. Hopefully I won't have to boot into Windows 7 again.  Thanks for your help.

---

