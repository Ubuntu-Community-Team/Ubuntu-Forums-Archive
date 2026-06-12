---
title: "Ubuntu 16.04 on Clevo P671RE6 with Skylake CPU (Intel i7-6700HQ)"
date: 2017-06-01
forum: General Help
---

### Post by numessanguis on 2017-06-01
I came across this post about running Ubuntu 15.10 on the Clevo P671RE6 with Skylake CPU (Intel i7-6700HQ) and Gsync:
[https://ubuntuforums.org/showthread.php?t=2314275](https://ubuntuforums.org/showthread.php?t=2314275)
and I was wondering what the current best combination of graphic drivers is.

Currently I can only run Ubuntu with multiple monitor support if I've set in my BIOS** graphics to DISCRETE**.
Installing Ubuntu 16.04 when it was just released was a huge pain in the ass, and I only succeeded by plugging and unplugging an external monitor (I guess to force the nVidia drivers) and modifying some options in configwiz for Unity.
I haven't been able to use my integrated graphics, which would be nice to reduce my laptop's power consumption.
Since I spend so much time to get something to work, I'm afraid of breaking my Ubuntu, and I rather not reinstall everything again.

Anyone with the same laptop has any advice on what driver combination is working well?
I don't want to disable my nVidia 970m, because I want to use it for for Deep Learning.

---

### Post by mörgæs on 2017-06-02
Have you tried 17.04? You don't have to let go of the old install, you can try the new one in a dual boot.

---

### Post by Scott Deagan on 2018-01-21
Sorry for the late reply - I'll still detail my experiences with this laptop just in case anyone is interested.

My laptop is a PC Specialist Defiance II, which is a re-badged Clevo P65_P67RGRERA:

```
[scott@def2:~]$ sudo dmidecode -t system
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 3.0.0 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: PC Specialist Limited
        Product Name: P65_P67RGRERA
        Version: Not Applicable                  
        Serial Number: Not Applicable                  
        UUID: 275BFA80-A763-0000-0000-000000000000
        Wake-up Type: Power Switch
        SKU Number: Not Applicable                  
        Family: Not Applicable                  

Handle 0x0011, DMI type 12, 5 bytes
System Configuration Options
        Option 1: Default string

Handle 0x0012, DMI type 32, 20 bytes
System Boot Information
        Status: No errors detected

```

I have searched the Interwebs far and wide for years trying to find a way to get dual monitors working in Intel GPU mode, but have never found solution. I came across a post in which someone explained to me why it wasn't possible: the output ports are hard-wired to the Nvidia GPU (I think s/he called it "Mux" or "Muxless", or something like that, from memory). I'm just thankful that it's not the other way around (i.e. external monitors only working in Intel GPU mode), as is the case with some Optimus laptops. For me, only having external monitor capability while the Nvidia driver is enable isn't so bad, as when attached to an external monitor I'm usually close to a power socket anyway.

When I swapped my SSD a couple of months ago, I decided to install Windows 10 just to see if Windows would support dual monitors in Intel GPU mode. I went in to the BIOS, switched the display driver over to "**MSHYBRID**", installed Windows 10, then plugged in a second monitor in to the HDMI port. The only setting that worked in Windows 10 was "mirrored" displays. It wasn't possible to have multiple independent displays.

I'm currently running Kubuntu 17.10 with a 4.13 kernel and the Nvidia 384.69 driver. I now permanently have my Defiance II in "MSHYBRID" mode, and I switch between the iGPU and dGPU using:

```
$ sudo prime-select nvidia
$ sudo prime-select intel
```

(and then logging out and logging back in again, or rebooting).

When installing (while in "MSHYBRID" mode), I had to set the "nomodeset" kernel option, and then immediately after the first reboot everything would just freeze. To get around this, I had to press ALT+CTRL+F1 the moment the login screen was displayed, and then add the following kernel parameter to /etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2015\" acpi=force"
```

(and then [COLOR=#696969][FONT=courier new]sudo update-grub[/FONT][/COLOR], and then reboot).

So my conclusion is it just cannot be done (although I would love to be proven wrong on this).

---

### Post by Scott Deagan on 2018-01-27
Looks like I was wrong (kind of). I just did a fresh install of KDE Neon (User Edition - Stable), and didn't install the nVidia drivers just to see what would happen. Everything worked great, although my laptop would freeze if I tried shutting it down or rebooting. This was rectified by adding the above acpi_osi="!Windows 2015" kernel parameter in my /etc/default/grub file.

My driver info:

```
scott@def2:~/Downloads$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: GM204M [GeForce GTX 970M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:126 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:127 memory:dd000000-ddffffff memory:a0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff
```

The **driver=nouveau** was expected, as was the **driver=i915**. However, when I ran [FONT=courier new]**sudo modinfo i915**[/FONT], I noticed this line:
```

parm:           enable_dp_mst:Enable multi-stream transport (MST) for new DisplayPort sinks. (default: true) (bool)
```

I plugged in a 2K monitor in to one of the mini-DisplayPorts, and to my surprise the external monitor fired up with my wallpaper! While it "worked" as a secondary display, it was very choppy, and it looked like the frame-rate was quite low (probably around 30FPS). Power usage also jumped from 12 Watts to 30 Watts, which kind of defeats the purpose (i.e. may as well use the Nvidia driver for dual monitors and have everything running smoothly at 60FPS - same power usage).

I'm now going to install the nvidia-384 driver to see what happens.

---

