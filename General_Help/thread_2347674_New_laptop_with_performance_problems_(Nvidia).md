---
title: "New laptop with performance problems (Nvidia?)"
date: 2016-12-27
forum: General Help
---

### Post by rodrigo-vilarinho on 2016-12-27
Hello!
I'm in serious need of some tech help. I'm very non technical but I will try to give as much info as possible. I just got myself a new Clevo laptop after my previous one, from a couple of years ago, burned down (almost literally!). However now I can't play games that I was playing quite ok in my previous laptop (Shadows of Mordor, Bioshock infinite, Life is Strange). I was not expecting a big improvement but I never thought it would be this bad performance. In general I feel this is performing worst than before. Now the question is if this is expected with this hardware or is there something I can do? For example: some technical problem that I'm not able to solve not related with hardware, problems with drivers, 3d acceleration, etc.

I'm running Ubuntu 16.10 with Unity.
New laptop:
Clevo P640RF (#Série P600 14"
LCD: 14" FHD (1920 × 1080) IPS
CPU: Intel Core i7 - 6700HQ 2.6GHz, 3.5GHz Turbo
Graphics card: NVIDIA GeForce GTX 965M 2GB GDDR5
RAM: 8GB DDR4 2133MHz - Kingston Hyper X
Hard drive SSD M.2: 275GB SSD M.2 Crucial MX300
Hard drive HDD 1: WD Scorpio Black 750GB 2.5 7200rpm 16MB SATA3

Old laptop: (was running Ubuntu 16.04 with Unity)
ClevoW230ssit
LCD: 13.3" LED FullHD 1920x1080 IPS Matte
CPU: Intel Mobile Core i7-4710MQ 2.5GHz 6MB
RAM: 1x G.Skill Ripjaws 8GB DDR3 1600MHz CL9
Graphics card: NVidia GeForce GTX860M 2GB DDR5
Hard drive HDD 1: WD Scorpio Black 750GB 2.5 7200rpm 16MB SATA3
Hard drive mSATA 1: Samsung 840 Evo 250GB SATA3 mSATA

I have the 375.26 Nvidia driver, and everything seems to be fine glxinfo and glxgears seams to work (as far as I can tell). 
```
glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 965M/PCIe/SSE2
OpenGL core profile version string: 4.5.0 NVIDIA 375.26
OpenGL core profile shading language version string: 4.50 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5.0 NVIDIA 375.26
OpenGL shading language version string: 4.50 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 375.26
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:

```
Glxgears gives around 3230 fps (in full screen about 300fps)

I also run a couple of other benchmarks:
Here are the benchmark results for both Unigine tests:

Unigine Valley Benchmark 1.0
FPS:7.1
Score:298
Min FPS:5.4
Max FPS:11.4

System
Platform:Linux 4.8.0-32-generic x86_64
CPU model:Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz (2591MHz) x8
GPU model:GeForce GTX 965M PCI Express 375.26 (2048MB) x1

Settings
Render:    OpenGL
Mode:1920x1080 fullscreen
Preset Custom
Quality High

Unigine Heaven Benchmark 4.0
FPS:7.2
Score:181
Min FPS:5.4
Max FPS:13.1

System
Platform:Linux 4.8.0-32-generic x86_64
CPU model:Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz (2592MHz) x8
GPU model:GeForce GTX 965M PCI Express 375.26 (2048MB) x1

Settings
Render:    OpenGL
Mode:1920x1080 fullscreen
Preset Custom
Quality High
Tessellation Disabled

Any help will be much appreciated!
And let me know if I can give you any more info.
Also if this is not the right place to get help about this kind of issue, please direct me to the right forum.
Thanks

---

### Post by mc4man on 2016-12-27
Those numbers are pretty bad, you may even beat them on the Intel iGPU.. As comp. on a 3+yr old 775m/i7-4700MQ using 16.04 would see an _avg_. of 24fps on high, 30 on medium for the valley test @ 1920x1080 fs.
Did this laptop come with windows, if so did you benchmark there? (- if not,  for comp. I've a similar hardware laptop, i7 - 6700HQ, GTX 960M 4GB that's windows only, could ck. but better to see on yours..

In any event if me I'd probably start over with 17.04, it's in dev but isn't any worse than 16.10 & should end up better if not already.
(- though wireless could be an issue for some in 17.04.

---

### Post by rodrigo-vilarinho on 2016-12-28
Thanks for the help. The laptop didn't had Windows so I have no idea how that would perform.

I'm a bit afraid to run 17.04 before release. I'm sure I will bump into some technical problems and I will have a hard time solving them. But do you think my performance problem is from the distro itself?

---

