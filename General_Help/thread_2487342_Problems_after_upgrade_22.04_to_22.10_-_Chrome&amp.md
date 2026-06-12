---
title: "Problems after upgrade 22.04 to 22.10 - Chrome&amp;Brave and flickering dual GPU laptop"
date: 2023-05-31
forum: General Help
---

### Post by pautorras on 2023-05-31
Hi folks,

In a new and powerfull laptop with Windows11 preinstaled and due to problems running virtual machines with vmware, I bought a 2nd nvme SSD disk to install ubuntu 22.04. The original disk with Windows11 it's not currently used.
With Ubuntu I achieved vmware problems, but I had problems with flickering in main screen (integrated with laptop). I installed Nvidia drivers vith apt, but flickering wasn't solved. In other screens (via HDMI cable or dockstation I never have problems).

In a forum I see that Ubuntu 22.10 fix flickering problems, so I decided to make an upgrade (not a fresh install).

Problems:
[LIST]
[*]It seems that flickering problems have not been solved (behavior is better but is not released at all). ¿Any idea?
[*]After upgrade to 22.10:
[LIST]
[*]Sound card was not detected. Dummy module. Problem solved.
[*]Web browsers like Brave and Google-chrome-stable don't render websites fine. Remove with purge and auto remove, and install again don't works. With Brave, creating a new profile it's seems to work but not 100%, maybe 75% works fine. With google Chrome I can't do anything, even chrome setting aren't available for any changes... ¿Do you know what can I do?
[/LIST]
[/LIST]


If I can't fix that, I'll return to Windows11, because with some manual steps it seems that vmware software works well right now.
But before return to Windows, I would like to give last chance to Ubuntu.

Can you help me?

Thanks!

---

### Post by MAFoElffen on 2023-06-01
Please post the results of these, posted within CODE Tags:
```

sudo lshw -C video | sed -e 's/ *resources/resources/' -e '/resources/ s/ [^ ]*:[^ ]*/ \n&/g' -e 's/resources:/       resources:/g' | sed 's/^ [^ ]/          &/'
apt list nvidia* --installed

```
To add CODE Tags (as I see you didn't use them in your original post), do this:

[noparse]```


Paste your output here...


```[/noparse]

---

### Post by pautorras on 2023-06-01
Hi @[COLOR=#000000]MAFoElffen,

See attached lshw output:
```

*-display                 
       description: VGA compatible controller
       product: Alder Lake-P Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 mode=2560x1600 resolution=2560,1600 visual=truecolor xres=2560 yres=1600
       resources: 
           iomemory:610-60f 
           iomemory:400-3ff 
           irq:182 
           memory:6102000000-6102ffffff 
           memory:4000000000-400fffffff 
           ioport:4000(size=64) 
           memory:c0000-dffff 
           memory:4010000000-4016ffffff 
           memory:4020000000-40ffffffff
  *-display
       description: 3D controller
       product: GA107M [GeForce RTX 2050]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: 
           iomemory:600-5ff 
           iomemory:610-60f 
           irq:201 
           memory:5f000000-5fffffff 
           memory:6000000000-60ffffffff 
           memory:6100000000-6101ffffff 
           ioport:3000(size=128)

```

And list nvidia:
```

nvidia-compute-utils-530/kinetic-updates,kinetic-security,now 530.41.03-0ubuntu0.22.10.2 amd64 [instal·lat, automàtic]
nvidia-dkms-530/kinetic-updates,kinetic-security,now 530.41.03-0ubuntu0.22.10.2 amd64 [instal·lat]
nvidia-driver-530/kinetic-updates,kinetic-security,now 530.41.03-0ubuntu0.22.10.2 amd64 [instal·lat]
nvidia-kernel-common-530/kinetic-updates,kinetic-security,now 530.41.03-0ubuntu0.22.10.2 amd64 [instal·lat, automàtic]
nvidia-kernel-source-530/kinetic-updates,kinetic-security,now 530.41.03-0ubuntu0.22.10.2 amd64 [instal·lat, automàtic]
nvidia-prime/kinetic,kinetic,now 0.8.17.1 all [instal·lat, automàtic]
nvidia-settings/kinetic,now 510.47.03-0ubuntu1 amd64 [instal·lat]
nvidia-utils-530/kinetic-updates,kinetic-security,now 530.41.03-0ubuntu0.22.10.2 amd64 [instal·lat, automàtic]

```


[/COLOR]Thanks in advance!

---

### Post by MAFoElffen on 2023-06-01
Hmmmm...

I am running Ubuntu 22.04.2, with the HWE stack, and have a nVidia GeForce GTX 1660 Ti, using nvidia-driver-530... but not having those problems. But my CPU on that workstation is AMD, and the discrete is Matrox G200 (not Intel).

With the HWE stack, I should be running the same as 22.10... Not knowing at the moment why yours is somehow different(?)

You only have Displays connected to your nVidia GPU right? In what resolutions? As X11 or Wayland? I do better with mine as using X11...

---

### Post by pautorras on 2023-06-01
Hi,

Web browsers problems fixed disabling hardware acceleration.
Now, I've to see if flickering issue is solved (the performance here is much better than 22.04 version, but I have to see). It's very annoying. I use X11 and flickering issues it's only affecting laptop main screen. With external screens there is no problem.

Thanks!

---

