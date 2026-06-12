---
title: "Intel graphics hd 3000"
date: 2014-04-17
forum: General Help
---

### Post by Navneet_Kumar on 2014-04-17
Can anyone helpme with the installation of intl graphics hd 3000 in ubuntu 13.10..in due steps.....???

---

### Post by 3rdalbum on 2014-04-17
> **Navneet_Kumar said:**
> Can anyone helpme with the installation of intl graphics hd 3000 in ubuntu 13.10..in due steps.....???

Hi Navneet, Ubuntu 13.10 already contains the drivers for Intel graphics, you do not need to install them.

Are you having problems with the version that is included in Ubuntu 13.10?

---

### Post by Navneet_Kumar on 2014-04-18
Yes.the problem is that in "About computer" no graphics card details are available.....if there are drivers installed by default,how can i see which of them are installed....>???

---

### Post by su:bhatta on 2014-04-18
Run this command in a terminal:
> sudo lshw -c video

It should give you details of the driver installed.
Under "Configuration: driver =   "

---

### Post by Navneet_Kumar on 2014-04-18
the output of the command is:
 *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4000(size=64)


Is it all right..??

---

### Post by su:bhatta on 2014-04-18
I don't have an Intel Graphics card so I don't know, But all seems right.
You driver version is  : > configuration: driver=i915 

---

### Post by Navneet_Kumar on 2014-04-18
thanxx sir......

---

### Post by bapoumba on 2014-04-18
I have an older intel video card and use the same driver.

---

### Post by Navneet_Kumar on 2014-04-18
Mine is Intel HD graphics 3000 as shown in windows.......

---

### Post by den_ on 2014-04-18
> **Navneet_Kumar said:**
> Mine is Intel HD graphics 3000 as shown in windows.......

Just relax, it is not that your card is using old drivers or something. If you encounter some problems, but I doubt you will, you can try newer drivers with newer kernel. You can get mesa and drivers from oibaf repo. Installation is easy, and if somethings breaks just hit ctrl + alt + F1, log in, and type sudo ppa-purge ppa:oibaf/graphics-drivers
Regarding newer kernels, just google something like Ubuntu 14.04 kernel 3.14.

Here is a launchpad link to oibaf: [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)
There is also a thread about it in phoronix phorums.

---

### Post by Navneet_Kumar on 2014-04-19
yes it was good to install the mesa drivers............:D

---

