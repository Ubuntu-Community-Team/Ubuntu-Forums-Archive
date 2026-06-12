---
title: "how to revcover or fall back?"
date: 2007-05-05
forum: General Help
---

### Post by Yaka on 2007-05-05
hi 

i installed ubunt fiesty 7.04 and after installing a few things via automatix and rebooting it gives a xconf error and i cant login just stuck on cmd prompt. 

is there way i can either fall back or recover prior to installing nvidia drivers?

---

### Post by matburton on 2007-05-05
You could simply change xorg.conf to use the old video drivers:

```
sudo vi /etc/X11/xorg.conf
```

and change "nvidia" to "nv" like below:

```

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce Go 6600]"
	Driver		"nv"
	BusID		"PCI:3:0:0"
	Option		"NoLogo"
EndSection

```

Save and then type:
```
sudo /etc/init.d/gdm start
```

Hope that helps ;)

---

### Post by Yaka on 2007-05-05
i have just tried that and still i get a failed x server gui error

---

