---
title: "how to show kernel configuration?"
date: 2008-04-30
forum: General Help
---

### Post by mrroland on 2008-04-30
Is there a way to see wich options are enabled in the kernel i'm using?
I need to now or these options are enabled:
802.1d Ethernet Bridging (in "Networking options") and "Universal TUN/TAP device driver support" (in "Network device support").

Thanks a lot for your help.

---

### Post by MacMan on 2008-04-30
> **mrroland said:**
> Is there a way to see wich options are enabled in the kernel i'm using?

IF I remember correctly (I'm not in front of my Linux box right now) there should be a copy of the actual kernel configuration in a pseudo-file in the /proc directory. It may be something like /proc/config.gz .

> **mrroland said:**
> I need to now or these options are enabled:
802.1d Ethernet Bridging (in "Networking options") and "Universal TUN/TAP device driver support" (in "Network device support").

I'm not sure about the Ethernet Bridging, but Tun/Tap should be available as a kernel module. To see if it's already loaded, you can:
```
lsmod | grep tuntap
```
Otherwise, you should be able to load it using:
```
sudo modprobe tuntap
```

Forgive me if it doesn't work, I don't have a linux shell to try now and it's been a while since I messed with the kernel modules. ;-)

Ciao.

---

### Post by mrroland on 2008-04-30
Thanks for the reply. 
Tuntap is not loaded and not available as module, so i gues i should install this.
There is no config.gz available. Should i enable something for this?
Regards,

---

### Post by ryanhaigh on 2008-04-30
The file is actuall in /boot and you can look at every enabled option using 
```

cat "/boot/config-`uname -r`" | less

```
or of course grep for what you want

---

