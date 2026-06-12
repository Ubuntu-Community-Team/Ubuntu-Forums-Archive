---
title: "[SOLVED] raw1394 won't mount"
date: 2007-10-22
forum: General Help
---

### Post by Amazona aestiva on 2007-10-22
I really need help:

So it just stopped working.

When I connect my camera, Ubuntu won't mount it. (there isn't raw1394 in /dev/)

I've tried to reinstall the "driver" with synaptic. Didn't work.

I've tried:
> sudo modprobe raw1394
Than there is the raw1394, but Kino and Kdenlive can't found a camcorder.

Any ideas?

Thanks.

PS: I MUST get back this to work!!!

---

### Post by roaldz on 2007-10-22
You don't have to mount a 1394 camera. Mounting is used for filesystems. You just access the devise rawly. If it's not working you should check if you have the right permissions to access and control the /dev/raw1394 device. That's all I can tell you:)

Good luck

Roald

---

### Post by Amazona aestiva on 2007-10-22
The system can't see my camera, so there is nothing that needs permission.

However I use sudo chown 666 /dev/raw1394 to record from it.

---

### Post by dionisis on 2007-10-22
Try the following as root:

```

mkdir -p /dev/ieee1394/dv/host0/PAL
mknod -m 666 /dev/ieee1394/dv/host0/PAL/in c 171 34
mknod -m 666 /dev/ieee1394/dv/host0/PAL/out c 171 35

```

It works for my camera in Kino... Hope it helps!

---

### Post by Amazona aestiva on 2007-10-22
> **dionisis said:**
> Try the following as root:

```

mkdir -p /dev/ieee1394/dv/host0/PAL
mknod -m 666 /dev/ieee1394/dv/host0/PAL/in c 171 34
mknod -m 666 /dev/ieee1394/dv/host0/PAL/out c 171 35

```

It works for my camera in Kino... Hope it helps!

No luck.... I think I need raw1394 not ieee1394.....

---

### Post by Amazona aestiva on 2007-10-22
There is the Firewire in my "lspci":
> nandor@nandor-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
[COLOR="Red"]01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)[/COLOR]
01:06.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GS (rev a1)
nandor@nandor-desktop:~$ 


---

### Post by Amazona aestiva on 2007-10-22
I've reinstalled Ubuntu quickly but it still doesn't work!!!!!!!:cry::cry::cry:

Help me!!!
PLEASE

---

### Post by Amazona aestiva on 2007-10-22
It's working! However I don't know why???

I simply reconnect everything.

Thanks anyway:)

---

