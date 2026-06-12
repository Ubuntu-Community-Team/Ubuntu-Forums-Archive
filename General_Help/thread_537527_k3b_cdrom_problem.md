---
title: "k3b cdrom problem"
date: 2007-08-29
forum: General Help
---

### Post by Rumpty on 2007-08-29
Running Kubuntu Feisty AMD64

When I try to start k3b in a terminal, nothing much happens, the k3b GUI never appears, and the CDROM drive locks, i.e. it will not eject when the button on the drive is pressed.

Here is the terminal output:

colin@ubuntu_amd:~$ k3b
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_RICOH_CD_R/RW_MP7240A to device /dev/hdc
/dev/hdc resolved to /dev/hdc
/dev/hdc is block device (0)
/dev/hdc seems to be cdrom
(K3bDevice::Device) /dev/hdc: init()

Sometimes an icon for Audio CD appears on the desktop after a minute or so, but not always! 

The same hardware worked fine in Dapper, also Kubuntu AMD64.

Any suggestions for a solution please?

---

