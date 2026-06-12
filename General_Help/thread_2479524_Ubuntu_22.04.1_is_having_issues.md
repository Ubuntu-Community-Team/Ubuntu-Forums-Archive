---
title: "Ubuntu 22.04.1 is having issues ?"
date: 2022-09-28
forum: General Help
---

### Post by aug7744 on 2022-09-28
Hello.
Thanks for read my topic.
I see users posting about Ubuntu 22.04 having problems with Nvidia video cards, Firefox problems and high cpu usage.
All problems are related with wrong settings and driver errors or wayland ?
Thanks for reply.
Have an nice day.

---

### Post by ActionParsnip on 2022-09-28
If you switch to Xorg is it better?

---

### Post by aug7744 on 2022-09-28
I not has used 22.04 yet.
Wayland is an protocol being an software not totally completed. Have issues.
Have much experience users saying to continue using xorg.

---

### Post by mIk3_08 on 2022-09-28
> **aug7744 said:**
> Hello.
Thanks for read my topic.
I see users posting about Ubuntu 22.04 having problems with Nvidia video cards, Firefox problems and high cpu usage.
All problems are related with wrong settings and driver errors or wayland ?
Thanks for reply.
Have an nice day.
I have used Ubuntu 22.04 for a month now. so far I haven't encountered these errors you mentioned. Regards and cheers.

---

### Post by ActionParsnip on 2022-09-28
What is the output of:
```

sudo dmidecode -t 1; sudo lshw -C display; lsb_release -a; uname -a

```
Thanks

---

### Post by poorguy on 2022-09-28
> **aug7744 said:**
> Hello.
I see users posting about Ubuntu 22.04 having problems with Nvidia video cards, 


I've  have problems with Nvidia graphics cards in all Linux distros because  ***the newer kernels anything beyond kernel 5.4 no longer supports the Nvidia proprietary graphics driver 340.108 ***and [I][B]the open source nouveau graphics driver doesn't always work.
[/B][/I]
I've never had any issues using Wayland it using ***Intel integrated graphics*** or*** Intel HD processor graphics*** or ***AMD APU graphics.***


> **aug7744 said:**
> Hello.
Firefox problems and high cpu usage.


Most of the major browsers are system resource hoggs.

Firefox Snap doesn't seem to use anymore system resources  that I've noticed than Firefox deb file.

 Firefox Snap does open slow the first time after a system reboot or a cold system power on but after that first time opens in seconds.

---

### Post by aug7744 on 2022-09-29
@poorguy

About video card using using driver 340.180 in recent kernels.
You have tried installing Nvidia binary driver ?
[https://www.nvidia.com/en-us/geforce/drivers](https://www.nvidia.com/en-us/geforce/drivers)



First install the dependencies
pkg-config
build-essential
libglvnd-dev
libglvnd-dev:i386
dkms

---

### Post by poorguy on 2022-09-29
> **aug7744 said:**
> @poorguy

About video card using using driver 340.180 in recent kernels.
You have tried installing Nvidia binary driver ?
[https://www.nvidia.com/en-us/geforce/drivers](https://www.nvidia.com/en-us/geforce/drivers)



First install the dependencies
pkg-config
build-essential
libglvnd-dev
libglvnd-dev:i386
dkms

Yes I tried and it was a disaster left me with a 640x480 unchangeable resolution.
The graphics card is a NVIDIA GT218 [GeForce 8400 GS and it's supported by the nouveau opensource driver.

I know my graphics card is considered to be outdated however the Nvidia proprietary graphics driver 340.108 was supported by the 5.4 kernel and worked very well.

I no longer use Nvidia graphics cards with Linux since newer kernels no longer support any of my cards.
Nvidia and Linux have always been problematic on my computers is just a bad combination and always will be imo.

Intel graphics and AMD/ATI graphics have always worked OOTB so I'll stay with a sure thing.

My Linux computers are Frankenstein boxes built from spare parts from my junk box and no two parts match so yep I use old graphics hardware.

For me the fun of using Linux is on something created from parts on hand and besides I'm cheap and don't want to buy anymore new computers.

---

### Post by aug7744 on 2022-09-29
Thanks sharing about GF8400 issues.
Not problem using "old" computers and "old" kernels.
Why you not use the nouveau driver ? GF8400 using CUDA 1.0 not has good performance.
Have you used the nouveau driver plus mesa drivers ? Mesa drivers works with Intel IGP.

---

### Post by corporal on 2022-09-29
May I offer a Fix to solve the problem of Installing Nvidia-Driver-340-108 into Ubuntu 22.04.1,  I have been trying for weeks to solve this, and found this fix for my old Macbook Pro 5,5
As you are aware the driver is missing in the Software/Additional drivers page, this fix will put it back again, and you will be able to install it from the Additional Drivers page:
Sadly I am unable to credit the original author, because I don't know who it was..

 Nvidia Graphics Driver for MacbookPro Nvidia-340-108

Add PPA Repository: ppa:kelebek333/nvidia-legacy

nvidia-updates-340 are available.

To install the PPA:

sudo add-apt-repository ppa:kelebek333/nvidia-legacy

sudo apt update

next, you need to install the packages:

sudo apt install nvidia-340-updates nvidia-340-updates-dev xorg-modulepath-fix

I hope this helps..

---

### Post by poorguy on 2022-09-29
> **aug7744 said:**
> 
Why you not use the nouveau driver ? GF8400 using CUDA 1.0 not has good performance.
Have you used the nouveau driver plus mesa drivers ? 

I am using the nouveau driver and it works okay however not as well as the Nvidia proprietary driver.

```


xubuntu@xubuntu:~$ sudo dmidecode -t 1; sudo lshw -C display; lsb_release -a; uname -a
[sudo] password for xubuntu: 
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 2.4 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: HP-Pavilion
    Product Name: GN556AA-ABA a6200n
    Version:  
    Serial Number: CNX7331FYD
    UUID: 00dc53c1-a6b9-1210-9450-f332c5b02741
    Wake-up Type: Power Switch
    SKU Number: GN556AA#ABA
    Family: 103C_53316J

  *-display                 
       description: VGA compatible controller
       product: GT218 [GeForce 8400 GS Rev. 3]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: /dev/fb0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=nouveau latency=0 resolution=1440,900
       resources: irq:24 memory:fb000000-fbffffff memory:d0000000-dfffffff memory:ee000000-efffffff ioport:ac00(size=128) memory:c0000-dffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy
Linux xubuntu 5.15.0-48-generic #54-Ubuntu SMP Fri Aug 26 13:26:29 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
xubuntu@xubuntu:~$ 


```

```


xubuntu@xubuntu:~$ inxi -Fxz
System:
  Kernel: 5.15.0-48-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: Xfce 4.16.0 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: HP-Pavilion product: GN556AA-ABA a6200n v: N/A
    serial: <superuser required>
  Mobo: ECS model: Nettle2 v: 1.0 serial: <superuser required>
    BIOS: Phoenix v: 5.12 date: 06/11/2007
CPU:
  Info: dual core model: AMD Athlon 64 X2 5600+ bits: 64 type: MCP
    arch: K8 rev.F+ rev: 3 cache: L1: 256 KiB L2: 2 MiB
  Speed (MHz): avg: 1000 min/max: 1000/2800 cores: 1: 1000 2: 1000
    bogomips: 11251
  Flags: ht lm nx pae sse sse2 sse3 svm
Graphics:
  Device-1: NVIDIA GT218 [GeForce 8400 GS Rev. 3] vendor: ASUSTeK
    driver: nouveau v: kernel bus-ID: 02:00.0
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: nouveau resolution: 1024x768
  OpenGL: renderer: NVA8 v: 3.3 Mesa 22.0.5 direct render: Yes
Audio:
  Device-1: NVIDIA MCP61 High Definition Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 00:05.0
  Device-2: NVIDIA High Definition Audio vendor: ASUSTeK
    driver: snd_hda_intel v: kernel bus-ID: 02:00.1
  Sound Server-1: ALSA v: k5.15.0-48-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: NVIDIA MCP61 Ethernet vendor: Hewlett-Packard
    type: network bridge driver: forcedeth v: kernel port: ec00 bus-ID: 00:07.0
  IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:
  Local Storage: total: 76.69 GiB used: 12.25 GiB (16.0%)
  ID-1: /dev/sda vendor: Hitachi model: HDS721680PLAT80 size: 76.69 GiB
Partition:
  ID-1: / size: 74.44 GiB used: 12.24 GiB (16.4%) fs: ext4 dev: /dev/sda3
  ID-2: /boot/efi size: 512 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/sda2
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 40.0 C mobo: N/A gpu: nouveau temp: 51.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 172 Uptime: 34m Memory: 7.76 GiB used: 1.13 GiB (14.6%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.2.0 Packages: 1488 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
xubuntu@xubuntu:~$ 


```

---

### Post by poorguy on 2022-09-29
> **corporal said:**
> May I offer a Fix to solve the problem of Installing Nvidia-Driver-340-108 into Ubuntu 22.04.1,  I have been trying for weeks to solve this, and found this fix for my old Macbook Pro 5,5
As you are aware the driver is missing in the Software/Additional drivers page, this fix will put it back again, and you will be able to install it from the Additional Drivers page:
Sadly I am unable to credit the original author, because I don't know who it was..

 Nvidia Graphics Driver for MacbookPro Nvidia-340-108

Add PPA Repository: ppa:kelebek333/nvidia-legacy

nvidia-updates-340 are available.

To install the PPA:

sudo add-apt-repository ppa:kelebek333/nvidia-legacy

sudo apt update

next, you need to install the packages:

sudo apt install nvidia-340-updates nvidia-340-updates-dev xorg-modulepath-fix

I hope this helps..

First thing I tried was installing the Nvidia driver from the PPA and again a disaster.

I finally just gave up and accept the fact that if I want to use the Nvidia graphics cards I have on hand than it's the nouveau driver as nothing else works.

The Nvidia drivers install however they don't/ won't properly and I'm left with a 640x480 unchangeable resolution.
I've spent too much time trying to find a solution and it just ain't worth the frustration of trying to make the unworkable work.

Eventually all computers and all computer hardware reaches a point where it is just no longer supported, frustrating yes however fact of life.

I appreciate your suggestion and the solution that worked on your old Macbook Pro 5,5 however this desktop is going back on the shelf.


Thanks

---

### Post by poorguy on 2022-09-29
> **corporal said:**
> 
Sadly I am unable to credit the original author, because I don't know who it was..


This may be the PPA you're refering to.

[https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy](https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy)


This is also the PPA I used.

[https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy](https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy)

---

### Post by grahammechanical on 2022-09-29
According to the Nvidia web site this seems to be the Nvidia driver for your GT 218 - Geforce 8400 GS. 

[https://www.nvidia.com/en-us/drivers/results/95154/](https://www.nvidia.com/en-us/drivers/results/95154/)

The Nvidia 304 driver also ran my Nvidia GT220 card. But Nvidia stopped supporting that video adapter and Ubuntu stopped offering the 304 driver and then also stopped offering the 340 driver and I had to run Ubuntu on the GT 220 with the Nouveau driver.

Is that problem here?

Regards

---

### Post by poorguy on 2022-09-29
> **grahammechanical said:**
> According to the Nvidia web site this seems to be the Nvidia driver for your GT 218 - Geforce 8400 GS. 

[https://www.nvidia.com/en-us/drivers/results/95154/](https://www.nvidia.com/en-us/drivers/results/95154/)

The Nvidia 304 driver also ran my Nvidia GT220 card. But Nvidia stopped supporting that video adapter and Ubuntu stopped offering the 304 driver and then also stopped offering the 340 driver and I had to run Ubuntu on the GT 220 with the Nouveau driver.

Is that problem here?

Regards

Exactly the same problem.

The Nouveau driver for the most works okay although running Google earth I sometimes experience a freezing display which requires a system restart and which did not happen with the Nvidia driver.

---

