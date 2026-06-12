---
title: "Booting problems with Ubuntu - boot repair failed"
date: 2021-05-15
forum: General Help
---

### Post by lpalazzotto on 2021-05-15
Hello,

I cannot boot my Ubuntu.

The URL of the boot repair report is at the following link:

[https://paste.ubuntu.com/p/kQDDvM5ntz/](https://paste.ubuntu.com/p/kQDDvM5ntz/)

[URL="https://paste.ubuntu.com/p/gYjFKSKW3T/"]
[/URL]Whereas here is the link to the report of the second boot repair where I  tried to clean up the old kernels: it still does not work.
[URL="https://paste.ubuntu.com/p/gYjFKSKW3T/"]
https://paste.ubuntu.com/p/gYjFKSKW3T/[/URL]

Can anyone help me to fix the issue?

Best,
Luca

---

### Post by oldfred on 2021-05-15
Are you manually editing repositories?
It says you have 20.04 but are updating from 21.04??
And it looks like you have a ppa that is invalid.

Can you boot into recovery mode.
You probably have to press escape right after UEFI/BIOS screen, but before grub menu.
If UEFI fast boot on, you may not have time to press any keys. Then you should be able to "cold" boot or full power down, not "warm" reboot where it remembers previous settings.

---

### Post by lpalazzotto on 2021-05-15
Hi Oldfred,

I booted from a USB with 21.04 to be able to run the boot repair tool, but it did not help much. But the machine has the 20.04 installed.
I tried to boot in recovery mode: it gives me various options, but when I press ok to finalize the booting, it stops after a couple of seconds and goes into a black screen with a blinking underscore.

---

### Post by oldfred on 2021-05-15
Usually best to use same version & flavor to make repairs.

That is often a video issue?
What video card/chip?

From live installer:
lspci -vnn | grep VGA -A 12
sudo lshw -c display 

#What is installed, if you can boot to terminal
dkms status

---

### Post by lpalazzotto on 2021-05-16
Here we are Oldfred: it took me a while, because I am now using an ISO with the 20.04 version.

Here is what I get:

```
~$ lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation UHD Graphics 630 (Mobile) [8086:3e9b] (prog-if 00 [VGA controller])
    DeviceName:  Onboard IGD
    Subsystem: Dell UHD Graphics 630 (Mobile) [1028:087c]
    Flags: bus master, fast devsel, latency 0, IRQ 143
    Memory at eb000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:04.0 Signal processing controller [1180]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [8086:1903] (rev 07)


```

and

```
~$ sudo lshw -c display
  *-display                 
       description: 3D controller
       product: GP107M [GeForce GTX 1050 Ti Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:144 memory:ec000000-ecffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:ed000000-ed07ffff
  *-display
       description: VGA compatible controller
       product: UHD Graphics 630 (Mobile)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:143 memory:eb000000-ebffffff memory:80000000-8fffffff ioport:4000(size=64) memory:c0000-dffff


```

in the next reply I will reply to your last question

---

### Post by lpalazzotto on 2021-05-16
And here is what I get when I boot to terminal
```

~# dkms status
amdgpu, 17.40-492261: added

```

---

### Post by oldfred on 2021-05-16
I do not understand amdgpu?
Do you also have an AMD gpu?

You show nVidia using nouveau or Intel with i915.

Typically with two video like nVidia & i915 you need the proprietary nVidia driver. 
Or you have to just use one or the other.

If you do not have AMD un-install that.
Then install the correct nVidia driver.

Whats available
dpkg -l | grep -i nvidia
Install nVidia If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX 

nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

### Post by lpalazzotto on 2021-05-16
Ok, I understood, but where should I perform this operation from? live ubuntu or boot to terminal and then doing it?

---

### Post by oldfred on 2021-05-16
Boot into terminal, otherwise from live installer you have to to do a full chroot.

---

### Post by lpalazzotto on 2021-05-16
ok:```
amdgpu-pro-uninstall
```from terminal did the trick.
back to normal.
Thank you Oldfred!

---

