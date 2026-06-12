---
title: "VMware Existing Windows."
date: 2007-02-28
forum: General Help
---

### Post by Nemix77 on 2007-02-28
Hi, I want to setup up VMware using my existing Windows installation.
I just got some questions regarding VMware:

1.  Does VMware offer direct hardware acceleration (ie: DRIVERS, Video, Sound, CPU, Ram, etc.)

2.  Am I gonna be able to use my peripherals in VMware Windows (ie:  CD/DVD burning, iPod, Floppy, etc.)

3.  Is is slow compared to a true boot into Windows. 

4.  What are the requirements to run VMware using existing Windows and I can manually set VMware to use a specific amount of resources  (ie: RAM, CPU,etc.)

5.  If I do use VMware to run my existing Windows would all changes made in VMware affect my real Windows partition.  (ie: Outlook Mail, MSN, add/remove software/DRIVERS, etc.)

6.  Is VMware exactly the same as true booting into Windows (ie:  I have to defrag, spyware, antivirs scan, etc.)

7. I have a genuine Windows so can I fetch updates in VMware Windows (ie: software upddates, ActiveX, WGA, etc.)

Just to clearify things I'm not gonna be using VMware for gaming, just apps (ie: Shockwave, WMV, MSN, Office, etc.)

---

### Post by tagra123 on 2007-02-28
I'm going to write a how-to for ubuntu.  I have a laptop setup dual boot and the VMware can access this same partition and boot it while in ubuntu Using different hardware profiles in windows. It works great and saves disk space.  You can access everything --mail, etc this way and yes changes installes, etc made on the Virtual machine will be there when you boot normally.  The drivers aren't a problem because of  windows ability to use hardware profiles.

VMWare doeshave some accel features, but they are just for testing -- they don't work that great.

It will be a littles slower but on a 500 mhz system or better with at least 256 of memory you'll barely notice.  More memory = better performance.

Windows WPA does look at hardware and I don't thing VM will change enough for it to be a problem... It wasn't on my dell.

---

### Post by Nemix77 on 2007-02-28
Thx.   :)

---

### Post by insub2 on 2007-03-04
> **tagra123 said:**
> I'm going to write a how-to for ubuntu.

This is exactly what i want to do and don't know how to do.  Could you post a link to your how-to when it is done.  Thanks.

---

### Post by crouton on 2007-04-17
> **Nemix77 said:**
> Hi, I want to setup up VMware using my existing Windows installation.
I just got some questions regarding VMware:

1.  Does VMware offer direct hardware acceleration (ie: DRIVERS, Video, Sound, CPU, Ram, etc.)

There is a set of drivers called 'VMWare Tools' that will accelerate Video/NIC/Keyboard/Mouse.  You won't be playing any 3D games on it, but it will work better than without.

> 2.  Am I gonna be able to use my peripherals in VMware Windows (ie:  CD/DVD burning, iPod, Floppy, etc.)

Floppy can be passed through.  Your iPod may work depending on its interface (there is USB passthrough).  CD/DVD burning, unlikely.

> 3.  Is is slow compared to a true boot into Windows. 

Booting a VM is actually much faster in some instances (usually when the VM is a clean Windows install or extra software has been removed.)

> 4.  What are the requirements to run VMware using existing Windows and I can manually set VMware to use a specific amount of resources  (ie: RAM, CPU,etc.)

You cannot set CPU with VMWare Server or Workstation (to my knowledge) as it shares the host physical machine's CPU time.  RAM can be specified.

> 5.  If I do use VMware to run my existing Windows would all changes made in VMware affect my real Windows partition.  (ie: Outlook Mail, MSN, add/remove software/DRIVERS, etc.)

If you convert your Windows install to a VM, everything that pertains to software is retained.  If it is looking at hardware (video card drivers, sound card, etc) you will likely want to remove it.

> 6.  Is VMware exactly the same as true booting into Windows (ie:  I have to defrag, spyware, antivirs scan, etc.)

If I understand your example, yes.  You would treat it just as you would a desktop machine.  I RDP into my Windows VMs as I do my physical Windows desktops.

> 7. I have a genuine Windows so can I fetch updates in VMware Windows (ie: software upddates, ActiveX, WGA, etc.)

Yes, the software remains the same so Windows Updates can be applied, Firefox will update, etc.

> Just to clearify things I'm not gonna be using VMware for gaming, just apps (ie: Shockwave, WMV, MSN, Office, etc.)

It will work well for those purposes.


I'm interested in how to 'share' the physical partition with a VM.  I know you can use a physical partition as the basis for a VM, but every time I've tried it under Linux the VMWare Server program complains that I don't have permissions.  So I just convert it using the VMWare Converter and run it as a plain VM.

---

