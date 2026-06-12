---
title: "All videos stutter"
date: 2022-07-27
forum: General Help
---

### Post by wombyte on 2022-07-27
[COLOR=#1A1A1B][B]I'm using Ubuntu 20.04, 64 bit, Desktop.
[/B]

When  I watch a video, it stutters very noticeable. This happens with every  video on every plattform (youtube, disney+, amazon video etc.) also with  DVD's or if I watch a video that I recorded with my smartphone and so  on.


[B]This  is a example on how it looks like: The video stutters (very noticeable  if you have a look at the statue of liberty in the video):
[/B][**[https://youtu.be/soLJwuoufU0](https://youtu.be/soLJwuoufU0)**]("https://youtu.be/soLJwuoufU0")
[I](This i not a recording stutter, it is exactly this way when I watch a video)
[/I]


I had a look at this one: [https://dragoshmocrii.com/ubuntu-20-04-stuttering-animations-video/](https://dragoshmocrii.com/ubuntu-20-04-stuttering-animations-video/)
But I have no such extensions installed. To make sure, I deactivated "Ubuntu AppIndicators", but did not solved it.
Any ideas?

[/COLOR]

---

### Post by mIk3_08 on 2022-07-27
> **wombyte said:**
> [COLOR=#1A1A1B][B]I'm using Ubuntu 20.04, 64 bit, Desktop.
[/B]

When  I watch a video, it stutters very noticeable. This happens with every  video on every plattform (youtube, disney+, amazon video etc.) also with  DVD's or if I watch a video that I recorded with my smartphone and so  on.


[B]This  is a example on how it looks like: The video stutters (very noticeable  if you have a look at the statue of liberty in the video):
[/B]**[https://youtu.be/soLJwuoufU0](https://youtu.be/soLJwuoufU0)**
[I](This i not a recording stutter, it is exactly this way when I watch a video)
[/I]


I had a look at this one: [https://dragoshmocrii.com/ubuntu-20-04-stuttering-animations-video/](https://dragoshmocrii.com/ubuntu-20-04-stuttering-animations-video/)
But I have no such extensions installed. To make sure, I deactivated "Ubuntu AppIndicators", but did not solved it.
Any ideas?

[/COLOR]
Have you ever tried to run glxgears in your system? Maybe you should try it. I haven't noticed any [COLOR=#1A1A1B]stutters in your movie on YouTube. Regards and cheers. [/COLOR]

---

### Post by ActionParsnip on 2022-07-27
What browser(s) have you tested?
What is the output of
```

sudo lshw -C display; sudo dmidecode -t 1

```
Thanks

---

### Post by wombyte on 2022-07-27
I tested it in Firefox and Chromium.

Output:
  *-display                 
       Beschreibung: VGA compatible controller
       Produkt: GP106 [GeForce GTX 1060 3GB]
       Hersteller: NVIDIA Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Version: a1
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress vga_controller bus_master cap_list rom
       Konfiguration: driver=nvidia latency=0
       Ressourcen: irq:137 memory:c3000000-c3ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:3000(Größe=128) memory:c4000000-c407ffff
  *-display
       Beschreibung: VGA compatible controller
       Produkt: Intel Corporation
       Hersteller: Intel Corporation
       Physische ID: 2
       Bus-Informationen: pci@0000:00:02.0
       Version: 03
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pciexpress msi pm vga_controller bus_master cap_list rom
       Konfiguration: driver=i915 latency=0
       Ressourcen: irq:135 memory:c2000000-c2ffffff memory:a0000000-afffffff ioport:4000(Größe=64) memory:c0000-dffff
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Micro-Star International Co., Ltd.
    Product Name: MS-7C89
    Version: 1.0
    Serial Number: Default string
    UUID: 7935d827-78b8-8f18-acec-d8bbc1084d6a
    Wake-up Type: Power Switch
    SKU Number: Default string
    Family: Default string

---

### Post by ActionParsnip on 2022-07-27
Have you tried Chrome? It may have bits that make it OK?

---

### Post by wombyte on 2022-07-28
> **ActionParsnip said:**
> Have you tried Chrome? It may have bits that make it OK?
Just tried it on two different systems, one frehs installed (with GTX 1660 super) and on my main system (GTX 1060). 
Both have the issue also with Chrome.
They also have the issue if I play a video that is stored locally or if I watch a DVD.

---

### Post by miguel001 on 2022-07-28
A more likely thing that would affect it is to try in xorg if in Wayland or vice versa if possible (I believe Ubuntu didn't fully disable Wayland with Nvidia).

Could be GPU driver, performance, or other issue though.

Its difficult to say where its stemming from. Should be streaming the file data from the drive to memory then the player should use it and the GPU and monitor should do their thing. Any issue in there could cause stutter.

---

### Post by MAFoElffen on 2022-07-29
Please run the UbuntuForums 'system-info" script in my signature line... When it asked you to upload a Pasrebin, select "y". Post the link to a post.

In the Graphics Section of that Report, if the Report says that you are using "Wayland" instead of "X11"... Then Logout, select the Gear Icon, and select "Xorg Xserver" as the session type... And also check which Video driver is being used. Make sure it is an NVidia driver...

I use NVidia GPU's. The NVidia Drivers seem to prefer Xorg XServer over Wayland... Just an observation.

---

