---
title: "Kubuntu ver.16.0.4.1"
date: 2016-08-08
forum: General Help
---

### Post by anon_private on 2016-08-08
I am running kubuntu (16.0.4.1) from a live dvd.

I am seeing whitish lines on occasions across the screen.

How can I eradicate these lines?

Thanks

---

### Post by Bucky Ball on 2016-08-08
Which video card are you using? You might need third-party drivers for the GPU which you may be able to install in a live session but they won't be there when you reboot. 

Have a look in 'Additional Drivers'. If there's something there for your GPU then installing that might fix the problem with a hard drive install. 

Give the output of this, please.

```
sudo lshw -C video
```

---

### Post by anon_private on 2016-08-09
At present, I am running Ubuntu ver 12 from a pendrive. I will run version 16.04.1 from the live DVD in a while and report the data. I intend to install 16.04.1 at a later stage. Will I be able to update the video drivers? If so, how would I install the package?

I have also noticed flashing on the screen and a propensity to diconnect from the ISP. Quite often it takes many attempts to login back in to the ISP. I hope that all these problems will resolve after updating any necessary software, after installation.

I had no problem with version 16.0.4 after updating version 14 on line. With the exception of a very long wait at bootup. Hence, the upgrade. I also managed to ruin this OS through attempts to resolve the long login time.

I could install either 16.0.4 or 16.0.4.1. I favour the latter because it is the latest version, providing that I can overcome the problems - lines, flashing, and disconnects.

In the meantinme, from the terminal within version 12 I see:

ubuntu@ubuntu:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: G72 [GeForce 7300 LE]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:dd000000-ddffffff memory:c0000000-cfffffff memory:de000000-deffffff memory:dfe00000-dfe1ffff
ubuntu@ubuntu:~$

---

### Post by Bucky Ball on 2016-08-09
Ok. I think you'd have issues running the 16.04 versions of Kubuntu or Ubuntu on that machine.

Try a live session with Xubuntu or Lubuntu 16.04 and see if you get the same issues.

---

### Post by anon_private on 2016-08-09
> **Bucky Ball said:**
> Ok. I think you'd have issues running the 16.04 versions of Kubuntu or Ubuntu on that machine.

Try a live session with Xubuntu or Lubuntu 16.04 and see if you get the same issues.

I have been running 16.04 for ages (installed) without any problems - other than the long booting time which has never been explained (others have noticed this phenomenon). The only question is can I obtain the video drivers to run 16.0.4.1. I agree that my symtoms probably occur due to an outdated driver.

Am I correct in assuming that kubuntu has all the necessary drivers to run the video requirements of the OS. If this is the case, then I should not have problems?

I note that the memeory requirements for the two versions are the same. In addition, I have the 32 bit version that caters for lower memory machines.

---

