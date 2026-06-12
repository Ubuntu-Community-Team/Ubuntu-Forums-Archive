---
title: "Installing NVIDIA drivers on Ubuntu 12.10 (gtx460)"
date: 2013-02-16
forum: General Help
---

### Post by Redronn on 2013-02-16
I've been trying to do this for hours, but nothing seems to work.

The result is always that I end up with a really low desktop resolution, and then have to uninstall the drivers.

---

### Post by papibe on 2013-02-16
Hi Redronn. Welcome to the forums ):P

Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by jackyboy633 on 2013-02-16
Hi there,

Tbe following tutorial helped me when i installed the nvidia drivers on my laptop:

[http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html]("http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html")


Hope this helps
Jackyboy633

---

### Post by Redronn on 2013-02-16
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device [1043:835d]
	Kernel modules: nouveau, nvidiafb

---

### Post by papibe on 2013-02-16
Thanks.

The nvidia driver is not loaded, and you are using nouveau.

Open 'Additional drivers' and select the 'nvidia-current'. Once it's installed, open a terminal and run:
```
sudo nvidia-xconfig
```
Then restart your computer.

If that does not work, please post the content of this file:
```
/var/log/Xorg.0.log
```
Paste it here: [http://pastebin.ubuntu.com/]("http://pastebin.ubuntu.com/") and post back the link to it.

Regards.

---

### Post by oldfred on 2013-02-16
Follow papibe instructions, but run this first.

       # You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic
    
I also had issues with nVidia and used my standard install procedures and they did not work, but once I installed kernel headers then the procedures worked.

---

