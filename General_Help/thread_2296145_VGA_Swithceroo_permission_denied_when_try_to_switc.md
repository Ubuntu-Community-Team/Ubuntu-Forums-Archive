---
title: "VGA Swithceroo permission denied when try to switch..."
date: 2015-09-23
forum: General Help
---

### Post by stefanoskikristijan on 2015-09-23
Hello, after many atempts to instal fglrx and after everything failed i found that i can switch using VGA SWITCHEROO. I have ubuntu 14.04 and kernel 3.13.0-63-generic. 
So when i run 
```
sudo grep -i switcheroo /boot/config-*
```
i get:
```
/boot/config-3.13.0-32-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.13.0-63-generic:CONFIG_VGA_SWITCHEROO=
```

Ok than i run:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```
And it shows:
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0
```

Ok than i try to Turn on my AMD Card using:
```
sudo echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
```

And here is where the permission is denied:
```
bash: /sys/kernel/debug/vgaswitcheroo/switch: Permission denied
```

Does anyone know how can i make my AMD to run properly, i need it to run only when i play games and than i will switch back to intel.

---

