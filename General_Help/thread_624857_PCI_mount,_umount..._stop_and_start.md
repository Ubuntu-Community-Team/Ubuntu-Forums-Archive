---
title: "PCI: mount, umount... stop and start"
date: 2007-11-27
forum: General Help
---

### Post by NT4usB on 2007-11-27
Can PCI slots be unmounted or stopped and restarted?
I have a SATA adapter card in a PCI slot that's hanging up and giving me grief. I'd like to be able to just kill it until it's convenient to restart and/or debug it.
Or, maybe by stopping and starting it, I can get it to correctly detect the attached HDD.
As it is now, I plug in a HDD, mount it, and all is fine.
Then I umount the HDD and plug in another HDD. Try to mount it but it's not recognized. Mount just hangs and have to kill it and it doesn't show up in /dev/ at all.
Open gparted to have a look but either gparted hangs or if it opens, it shows the drive info for the HDD that was umounted. Refreshing doesn't change it.
So, how do I refresh a IDE?
This is on the Edgy box if you're looking for specs.

---

### Post by kidders on 2007-11-28
Hi there,

Afaik, PCI hotplugging requires compatible hardware, as well as the appropriate software. For example, the feature is activated in my Edgy ...```
$ grep HOTPLUG_PCI /boot/config-2.6.15-29-server
CONFIG_HOTPLUG_PCI_PCIE=m
# CONFIG_HOTPLUG_PCI_PCIE_POLL_EVENT_MODE is not set
CONFIG_HOTPLUG_PCI=m
CONFIG_HOTPLUG_PCI_FAKE=m
CONFIG_HOTPLUG_PCI_COMPAQ=m
CONFIG_HOTPLUG_PCI_COMPAQ_NVRAM=y
CONFIG_HOTPLUG_PCI_IBM=m
CONFIG_HOTPLUG_PCI_ACPI=m
CONFIG_HOTPLUG_PCI_ACPI_IBM=m
CONFIG_HOTPLUG_PCI_CPCI=y
CONFIG_HOTPLUG_PCI_CPCI_ZT5550=m
CONFIG_HOTPLUG_PCI_CPCI_GENERIC=m
CONFIG_HOTPLUG_PCI_SHPC=m
# CONFIG_HOTPLUG_PCI_SHPC_POLL_EVENT_MODE is not set
```... but I wouldn't expect it to actually work properly because (a) kernel support for PCI hotplugging is experimental, and (b) my motherboard can't handle it anyway.

The same applies to hotplugging block devices. For instance, most BIOSes don't support hotplugging on an IDE bus. Your hardware manufacturer should be able to tell you more.

---

### Post by NT4usB on 2007-11-29
Thanks. I hadn't thought about the hotplug angle. I was thinking of it like a service (in Windows) that could be stopped and started.
But then, PCI is not a service in Windows so, what was I thinking.
Anyway, I finally got the WD750 mounted along with the other drive. Appears If I leave them alone and don't go all musical drives, they behave.

---

### Post by kidders on 2007-11-30
It's good to hear things are working for you. :-)

---

