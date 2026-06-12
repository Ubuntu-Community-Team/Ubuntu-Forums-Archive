---
title: "Netconsole not working"
date: 2008-03-21
forum: General Help
---

### Post by Ramses de Norre on 2008-03-21
Hi

I'm trying to monitor the boot process of a ubuntu machine in my network using netconsole. The machine to be monitored is booted with this kernel line:
```
kernel  /boot/vmlinuz-2.6.22-14-generic root=UUID=<snip> ro netconsole=4444@192.168.123.193/eth1,6666@192.168.123.106/00:13:D3:8B:9E:89 vga=794
```
With 192.168.123.193 the ip of the local machine, 192.168.123.106/00:13:D3:8B:9E:89 the ip and mac address of the remote machine.

The netconsole module is available, I was able to modprobe it, and I've added it to /etc/initramfs-tools/modules and did a ```
dpkg-reconfigure linux-image-2.6.22-14-generic
``` I'm using netcat on the monitoring machine like this: ```
nc -l -p 6666 -u
``` but I'm not getting any output... 
Does anyone see a flaw in my setup?

---

### Post by Ramses de Norre on 2008-03-23
Anyone? (Damn a post gets out of sight fast on these forums...)

---

