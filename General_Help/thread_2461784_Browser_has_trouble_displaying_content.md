---
title: "Browser has trouble displaying content"
date: 2021-05-06
forum: General Help
---

### Post by nthnwdhs on 2021-05-06
When I use a browser the window has  trouble displaying the content (see this video I made:  [https://www.youtube.com/watch?v=X5gdpTd8hEM](https://www.youtube.com/watch?v=X5gdpTd8hEM)).  If I ignore it, it gets worse and eventually the whole  screen freezes requiring a computer reset.

It's kind of flicker / partial freeze type of thing where lines are shown over different parts of the screen, parts of pictures are repeated etc..

It was like  this when I got the computer (Ubuntu 16), then when it upgraded to  Ubuntu 18 the problem went away, then with the current version (20.04)  the problem came back.

On Ubuntu 16 I tried various things I've read from other's problems on other forums to do with with screen flicker and screen freeze, but I can't remember exactly what they were (and nothing worked).

When I logged in I was getting an error saying the monitors couldn't be configured (but that has gone after the computer had an update last night).

Also before last night's update, when I reduced the screen resolution, the whole screen turned into a jigsaw puzzle, bits of the screen in squares all over the place.  This doesn't happen anymore.

I have two computers which have shown the same symptoms through the Ubuntu upgrades.

Thanks for any help.

---

### Post by &amp;KyT$0P# on 2021-05-07
"a browser" always meaning Firefox, as shown in your video?
Have you tried [disabling hardware acceleration in Firefox]("https://support.mozilla.org/en-US/kb/troubleshoot-extensions-themes-to-fix-problems#w_turn-off-hardware-acceleration")?

---

### Post by nthnwdhs on 2021-05-08
> **halogen2 said:**
> "a browser" always meaning Firefox, as shown in your video?
I have the same problem in Chrome also, but not in Midori (never heard of Midori before but downloaded it and gave it a try, and it was good)

Actually, playing a you tube video in Midori, while using Firefox, was worse for Firefox than just using Firefox.

> Have you tried [disabling hardware acceleration in Firefox]("https://support.mozilla.org/en-US/kb/troubleshoot-extensions-themes-to-fix-problems#w_turn-off-hardware-acceleration")?

I'm not sure if I tried it before so I tried if for Chrome and Firefox but unfortunately it didn't make much difference.

---

### Post by nthnwdhs on 2021-05-08
As it turns out Midori just froze my screen a couple of times so it is affected, just in a different way.

---

### Post by &amp;KyT$0P# on 2021-05-08
Can you please post the output of running this command in Terminal to show what kind of graphics setup you got -
```
inxi -Gxxz
```

If you don't have inxi, first install it with
```
sudo apt-get install inxi
```

---

### Post by grahammechanical on 2021-05-08
Are you using Wayland or X Server? An Open source or proprietary video driver? is the kernel 5.4 or 5.8? There are alternatives that can be tried. Do they make a difference? What are the specifications for CPU, RAM, and video adapter?

The solution for Firefox may be to turn on WebRender.

[https://www.omgubuntu.co.uk/2020/07/firefox-enable-webrender-linux](https://www.omgubuntu.co.uk/2020/07/firefox-enable-webrender-linux)

Regards

---

### Post by nthnwdhs on 2021-05-11
> **halogen2 said:**
> Can you please post the output of running this command in Terminal to show what kind of graphics setup you got -
```
inxi -Gxxz
```

So here is the result from my computer:
```

Graphics:
  Device-1: AMD Picasso driver: amdgpu v: kernel bus ID: 09:00.0
  chip ID: 1002:15d8
  Display: x11 server: X.Org 1.20.9 driver: amdgpu,ati
  unloaded: fbdev,modesetting,vesa compositor: marco
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: AMD RAVEN (DRM 3.35.0 5.4.0-72-generic LLVM 11.0.0)
  v: 4.6 Mesa 20.2.6 direct render: Yes

```
[QUOTE=grahammechanical]Are you using Wayland or X Server?[/QUOTE]
I'm pretty sure I've tried both and I'll check this when I'm at my computer again.  I'm away from it for about a week so when I get back I'll go through your questions.

---

### Post by nthnwdhs on 2021-05-29
> **grahammechanical said:**
> Are you using Wayland or X Server?  
 I'm not sure what you mean here now, I thought I did but now I'm not sure.  When I log in I have a choice of desktops - mate, ubuntu and ubuntu on wayland.  So I've tried all three desktops and there's no difference. But it seems my 'server' is X.Org all the time, so I guess I'm using X Server (see the out put of inxi below when I'm using Wayland)
 
 
 ```
-->inxi -Gxxz

 Graphics:
   Device-1: AMD Picasso driver: amdgpu v: kernel bus ID: 09:00.0  
   chip ID: 1002:15d8 
   Display: wayland server: X.Org 1.20.9 driver: amdgpu,ati  
   unloaded: fbdev,modesetting,vesa compositor: gnome-shell  
   resolution: 1920x1080~60Hz  
   OpenGL: renderer: AMD RAVEN (DRM 3.35.0 5.4.0-70-generic LLVM 11.0.0)  
   v: 4.6 Mesa 20.2.6 direct render: Yes  
 -->

``` 
 
 > An Open source or proprietary video driver?

 Open source - Amdgpu
 
 
  > is the kernel 5.4 or 5.8? There are alternatives that can be tried. Do they make a difference?
The kernel if 5.4 - I saw the following page at some stage [https://askubuntu.com/questions/1305703/why-is-my-ubuntu-laptop-freezing-suddenly](https://askubuntu.com/questions/1305703/why-is-my-ubuntu-laptop-freezing-suddenly) and on it someone fixed a screen flicker / computer freeze by loading an older version of the kernal  in the "Advanced Options for Ubuntu" option.  I went to try this but I could only choose between 5.4.0-72 and  5.4.0-70, and they make no difference.  I'm using 5.4.0-72 - I thought it was 5.8.x but it's not - maybe I should try 5.8?  (How do I do this? / Can I do this?)
 > What are the specifications for CPU, RAM, and video adapter?
See below:
 ```
-->inxi -C

 CPU:
   Topology: Quad Core model: AMD Ryzen 3 3200G with Radeon Vega Graphics  
   bits: 64 type: MCP L2 cache: 2048 KiB  
   Speed: 1257 MHz min/max: 1400/3600 MHz Core speeds (MHz): 1: 1257 2: 1257  
   3: 1257 4: 1258  
 -->
 -->sudo inxi -m
 [sudo] password for nathan:  
 Memory:
   RAM: total: 13.68 GiB used: 2.40 GiB (17.6%)  
   Array-1: capacity: 128 GiB slots: 4 EC: None  
   Device-1: DIMM 0 size: No Module Installed  
   Device-2: DIMM 1 size: 8 GiB speed: 2666 MT/s  
   Device-3: DIMM 0 size: No Module Installed  
   Device-4: DIMM 1 size: 8 GiB speed: 2666 MT/s  
 -->
 -->sudo lshw -C display
   *-display                  
        description: VGA compatible controller
        product: Picasso
        vendor: Advanced Micro Devices, Inc. [AMD/ATI]
        physical id: 0
        bus info: pci@0000:09:00.0
        version: c9
        width: 64 bits
        clock: 33MHz
        capabilities: pm pciexpress msi msix vga_controller bus_master cap_list rom
        configuration: driver=amdgpu latency=0
        resources: irq:61 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fcc00000-fcc7ffff memory:c0000-dffff
 -->

``` 
 
>  The solution for Firefox may be to turn on WebRender.

[URL="https://www.omgubuntu.co.uk/2020/07/firefox-enable-webrender-linux"]https://www.omgubuntu.co.uk/2020/07/...ebrender-linux 
[/URL]

 
No difference :(

Let me know if there's enough info here...
Thanks

---

