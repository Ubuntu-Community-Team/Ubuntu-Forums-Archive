---
title: "dhcp error"
date: 2015-08-08
forum: General Help
---

### Post by sniper8752 on 2015-08-08
I am trying to setup my netgear wireless usb device to connect to my wifi.  I also have ethernet plugged into my desktop, but disabled that so it should not be connecting to it.  In the USB of settings, I've added the usb filter.  I turn on the VM machine, then when I am in, I plug in the usb device, and do ifup wlan0.  if attempts several dhcpdiscovers.  it then says that there were no dhcpoffers received.  no working leases in persistent database-sleeping.  any ideas on how to fix this?  when I do ifdown wlan0, my vm machine then really begins to lag and slow down.

---

### Post by Vladlenin5000 on 2015-08-08
How to fix what exactly?

1. If the USB dongle is being used by/installed in the host then what happens is the network is usually bridged. As such, your concern should be how to properly setup the network/internet connection on the host and on the host only.
2. You can make the VM use a different network/internet connection for sure - and there are a few instances where that's the desired configuration - then you have to make sure the guest OS supports the WiFi device you just assigned to the VM.

Your post is quite confusing because you don't actually say what's the purpose of such setup and what issues are you really having. We don't have crystal balls here nor are we psychics so, please, describe your setup and give information regarding the hardware you're dealing with.

---

### Post by sniper8752 on 2015-08-08
I guess what I am looking to do is have the VM exclusively use the usb wifi adapter.  I would like to use Wireshark, so I need to connect my adapter to the VM so that it can use it.  Hopefully this helps.  Please let me know if I can provide any other information.

---

### Post by Vladlenin5000 on 2015-08-08
If so it all depends on the guest OS.

---

### Post by sniper8752 on 2015-08-08
The guest OS is Ubuntu.

---

### Post by SeijiSensei on 2015-08-08
If you are using VirtualBox, you'll need to install the Extension Pack in the guest then configure the USB devices in the VirtualBox manager.  USB is a proprietary standard and thus cannot be supported in the open VirtualBox code.  The Extension Pack includes the proprietary modules.

I've found USB access somewhat unreliable.  You'll also probably have to blacklist the Linux driver module for your adapter so Linux doesn't try to grab it for itself.

I think you're much better off using a bridged arrangement.  The VM's virtual adapter will get a unique IP address that you can monitor.  You can even assign it an arbitrary MAC address if you need to.

---

### Post by sniper8752 on 2015-08-08
I installed it.  I tried using eth0 for what I am trying to do, but it must be a Wlan interface for it to work.

---

