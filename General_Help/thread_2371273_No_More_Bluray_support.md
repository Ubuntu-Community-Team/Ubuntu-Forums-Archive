---
title: "No More Bluray support?"
date: 2017-09-12
forum: General Help
---

### Post by ebutts531 on 2017-09-12
I have a Bluray superdrive. Just a month ago I was able to have the bluray mount. Now it doesn't. Using 17.04. I do update frequently. No sure if it is related to an update. I can auto mount cd's and dvd's no problem with the same drive. I have no acces to the bluray disk whatsoever. Most solutions I have found though only work if the disk mounts. Mine does not. Makemkv identifies the disk drive just fine but tells me there is no disk. This now happens for all my blurays. Not just the newer ones. Is this more likely a drive failure (don't see how if it reads data and dvd disks ok) or is this more likely a kernel issue or something relating to an update? Thanks in advance for any suggestions you might have. 

 OS device name: /dev/sr0
Manufacturer: TSSTcorp
Product: DVDWBD SH-B123L
Revision: SB04
Serial number: R8496GGB500539

Intel® Core™ i7-7700K CPU @ 4.20GHz × 8 
GeForce GTX 1080/PCIe/SSE2
Ubuntu 17.04 64-bit - gnome

---

### Post by mc4man on 2017-09-13
Do you have access to an unprotected Blu-ray disc? If so try it.
Otherwise put a disc in, see if anything is reported in bottom of  /var/log/syslog

You could also try a live session of 16.04.3 image. It uses zesty kernel or 16.04.2 image, it uses yakkety kernel

---

### Post by ebutts531 on 2017-09-13
Hey mc4man. Thanks for the advice on the syslog. I do not have a bluray disc. However while trying to look at the syslog and retrying the disc, it did work. But only once. Now I can't get it to work again. Below is what I have when it did work for "Die Hard". After that is what syslog reports when it fails on reinstalling disc. I don't know what I'm looking at really. 

Sep 13 17:57:06 eric-Wild-Dog kernel: [ 1185.253264] UDF-fs: INFO Mounting volume 'DIE_HARD', timestamp 2007/09/07 01:31 (1000)
Sep 13 17:57:06 eric-Wild-Dog udisksd[2180]: Mounted /dev/sr0 at /media/ebitz/DIE_HARD on behalf of uid 1000
Sep 13 17:57:06 eric-Wild-Dog nautilus[3979]: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Sep 13 17:57:06 eric-Wild-Dog dbus[1059]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Sep 13 17:57:06 eric-Wild-Dog nautilus[3979]: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Sep 13 17:57:06 eric-Wild-Dog systemd[1]: Starting Hostname Service...
Sep 13 17:57:06 eric-Wild-Dog dbus[1059]: [system] Successfully activated service 'org.freedesktop.hostname1'
Sep 13 17:57:06 eric-Wild-Dog systemd[1]: Started Hostname Service.
Sep 13 17:58:10 eric-Wild-Dog udisksd[2180]: Cleaning up mount point /media/ebitz/DIE_HARD (device 11:0 is not mounted)
Sep 13 17:58:10 eric-Wild-Dog udisksd[2180]: Unmounted /dev/sr0 on behalf of uid 1000
Sep 13 17:58:32 eric-Wild-Dog NetworkManager[1074]: <info>  [1505339912.2359] device (wlp9s0): set-hw-addr: set MAC address to 32:C2:05:0E:35:0C (scanning)
Sep 13 17:58:32 eric-Wild-Dog kernel: [ 1271.013476] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready
Sep 13 17:58:32 eric-Wild-Dog NetworkManager[1074]: <info>  [1505339912.2873] device (wlp9s0): supplicant interface state: scanning -> disconnected
Sep 13 17:58:32 eric-Wild-Dog NetworkManager[1074]: <info>  [1505339912.2930] device (wlp9s0): supplicant interface state: disconnected -> inactive
Sep 13 17:58:32 eric-Wild-Dog wpa_supplicant[1429]: wlp9s0: Reject scan trigger since one is already pending

---

