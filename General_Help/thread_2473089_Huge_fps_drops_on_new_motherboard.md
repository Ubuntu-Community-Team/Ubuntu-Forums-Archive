---
title: "Huge fps drops on new motherboard"
date: 2022-03-23
forum: General Help
---

### Post by sabrina1 on 2022-03-23
Hello. 
I have Ubuntu 20.04 (5.13.0-35.40~20.04.1-generic 5.13.19). After switching my motherboard and CPU to Asrock B450-Pro4 and AMD Ryzen 3 3100, i started to get fps drops from time to time. It went to 1fps or something like that. I tried to reinstall system, but it didn't help. Is there any other things i can use to try to fix this? My HW:
Ryzen 3100
Asrock b450 pro 4
Ssd Kingdian 240gb (status is PERFECT according for HDD sentinel)
1 tb hdd (also perfect)
2x8 gb dimm Samsung

---

### Post by MAFoElffen on 2022-03-23
Switching...? You said the "TO". What was the from?

Next you refer to "fps", which is a measurement of video 'frames per second'... Which AMD Ryzen 3100 CPU is just that. It is not an APU, with internal video, but rather requires a video card. 

What is your video on old and new?

---

### Post by sabrina1 on 2022-03-23
Old motherboard is gigabyte 990xa-ud3. Video is Gigabyte GeForce GTX 660 on both. I measured fps with glxgears, which may not be completely accurate, but it did detect lower framerate when i saw lags. My monitor is 60hz so i expect to see 300 frames per 5 seconds, but it occasionally drops to like 240 frame per 5 seconds, when freezing basically for a whole second. Usually it drops to like 270 which is still noticeable as if my monitor goes to 50hz or less for couple of seconds. And it doesn't depend on cpu or gpu load, just happens by itself.

---

### Post by MAFoElffen on 2022-03-23
60 Hz at what resolutions? You are just measuring via glxgears?

I have dual boot, so Win10 and Ubuntu... On Win10, I use NVidia Geforce Experience to be able to display the FPS while in Gameplay....

Looking up tested benchmarks on your Video GPU, I see it is rated at 60 fps, which is higher than your expectations. On Ryzen 3, I see it tests at about 48 fps on the average. The refresh rate of a resolution... supposedly the refresh rate of a display has nothing to do with how many frames per second a GPU can generate, though you would think that resolution/refresh rate would have something to do with that. That sounds like it might to me, but others say that it is separate, and unrelated.

I would test mark it on a benchmark suite. That is what I do. I support the Linux Graphics Layer, and though I use glxgears to help people diagnose graphics problems (because that is what they might have access to), I haven't found it consistent enough and generating enough of a load load, for bench-marking. I use the Phoronix Test Suite for Bench Marching machine setups and hardware stress tests.

I'm a Developer, as well as an IT Professional that has to support people's whims and support issues. I have some standards which I try to test to... I try to get an accurate picture of what that might be.

---

### Post by miguel001 on 2022-03-29
glxgears is a part of mesa thus it should be heavily dependent on mesa. The board drivers are not the same as well which could interact with performance.

Either way, glxgears is old and not really relevant today. The benchmark will be highly specific and not necessarily correct. It could also have bugs.

---

### Post by ajgreeny on 2022-03-29
As others have said, glxgears is old, and useless as a benchmarker.

Nevertheless you will probably see very different output if you use command ```
vblank_mode=0 glxgears
```
Still rather meaningless, but I offer this just for information.

---

### Post by him610 on 2022-03-29
You could try this...[https://www.howtoforge.com/tutorial/linux-gpu-benchmark/]("https://www.howtoforge.com/tutorial/linux-gpu-benchmark/")
download it -
```

sudo apt-get install glmark2

```
Then run it -
```
glmark2
```

Added: Check your cables.

---

