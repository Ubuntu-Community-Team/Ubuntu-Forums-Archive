---
title: "Wireless disappears after todays' kernel update!"
date: 2008-06-19
forum: General Help
---

### Post by tbraun on 2008-06-19
Hello!

The update manager informed me that I needed to upgrade my kernel (and some of the related other modules). I ran version 2.6.22-14, and the update was for 2.6.22-15.

After the update I rebooted as instructed - just to find that my wireless was gone! Even after another reboot the problem wasn't fixed. I had to boot back into the old kernel before wireless came back up again.

For what it's worth, I'm running 7.10 on a Dell D820 with standard Intel wireless chips.

Any idea what's going on? What can I do to fix the problem? Has anyone else experienced this?

Thank you very much...

---

### Post by ibutho on 2008-06-19
Did you compile the wireless driver yourself? If so, everytime there is a kernel update, you have to recompile the driver to work with the new kernel.

---

### Post by ians1 on 2008-06-19
Yes I have had this, reported in another thread.  Needed to re-do the WPA/WEP password/key and reconfigure the network settings, works fine for me but others are still not even getting a wireless adapter/connection showing.

No indications have been given as to why this is happening.

I have Hardy Heron 32bit 8.04 with a C+W USB Wireless adapter with ndiswrapper using the Windows .inf file rt73 and a Netgear router with WPA-Personal enabled with a Preshared Key PSK.:confused:

ian

---

### Post by tbraun on 2008-06-19
> **ibutho said:**
> Did you compile the wireless driver yourself? If so, everytime there is a kernel update, you have to recompile the driver to work with the new kernel.

No, nothing like this. I picked the hardware config of the computer with Linux in mind, so I chose plain Intel wireless hardware, which was well supported. When I installed Ubuntu on it, it worked right out of the box, as I had hoped for. Even subsequent kernel updates had never caused this problem. It's something specific to this particular kernel update now...

---

### Post by tbraun on 2008-06-19
> **ians1 said:**
> Yes I have had this, reported in another thread.  Needed to re-do the WPA/WEP password/key and reconfigure the network settings, works fine for me but others are still not even getting a wireless adapter/connection showing.



How did you 'reconfigure the network settings'? And I don't think that WPA/WEP keys had anything to do with it, since ifconfig didn't even show the wireless interface at all.

It was basically as if the OS didn't realize that there was a wireless device at all in the computer.

---

### Post by ians1 on 2008-06-20
The network settings reset whenever you change WPA/WEP (dont forget I am new to this) I did it through the gui.

The wireless adapter was always showing but the connectivity just vanished after the update. As I said above, some others reported what you have, ie no adapter showing at all.

ian

---

### Post by Zorael on 2008-06-20
What's the output of this, entered in a terminal?
```
$ lshw -C network
```

---

### Post by Wetscoast Gus on 2008-06-20
bump

---

### Post by ians1 on 2008-06-21
> **Zorael said:**
> What's the output of this, entered in a terminal?
```
$ lshw -C network
```

```
ians@ians-unix:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  

```

but dont forget mine is working now!

ian

---

### Post by Zorael on 2008-06-21
> **ians1 said:**
> ```
ians@ians-unix:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  

```
Uh, seems like you copied it too early. It says those "PCI (sysfs)", "CPUID", "SCSI" and similar messages when it's probing your hardware. The following output should look something like this.

```
$ lshw -C network
WARNING: you should run this program as super-user.
[B]  *-network
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:04:b8:f6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip=10.0.0.102 latency=64 mingnt=255 module=e1000 multicast=yes[/B]
```

If it still doesn't appear *at all*, then your card isn't being detected, for some reason. Not a matter of drivers. I'd boot up a live cd and see if it works there; if it doesn't, then it's likely hardware failure.

---

### Post by ians1 on 2008-06-22
Mines working OK and had never disappeared, it was the chap above who had this problem.

It was my WPA/WEP keys that disappeared after the update.

ian

---

