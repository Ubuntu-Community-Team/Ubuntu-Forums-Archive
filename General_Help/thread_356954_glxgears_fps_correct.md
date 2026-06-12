---
title: "glxgears fps correct??"
date: 2007-02-09
forum: General Help
---

### Post by krotaz on 2007-02-09
Hi.

I just have a question.

Yesterday I tried Ubuntu 64 bits on my x2 3800+ and installed the nvidia drivers with Automatix. I execute "glxgears -printfps" and the avegrage was between 16000 and 17000. Today I installed Ubuntu for 32 bits and again used Automatix for the driver.

This are the results of the glxgears -printfps

WITH A 1152X864 RESOLUTION
krotaz@Trespatines:~$ glxgears -printfps
43814 frames in 5.0 seconds = 8762.722 FPS
55838 frames in 5.0 seconds = 11167.513 FPS
66783 frames in 5.0 seconds = 13356.490 FPS
79697 frames in 5.0 seconds = 15939.339 FPS
71978 frames in 5.0 seconds = 14395.525 FPS
76382 frames in 5.0 seconds = 15276.309 FPS
63849 frames in 5.0 seconds = 12745.199 FPS
45913 frames in 5.0 seconds = 9182.484 FPS
46128 frames in 5.0 seconds = 9225.443 FPS
46118 frames in 5.0 seconds = 9223.580 FPS
45403 frames in 5.0 seconds = 9080.572 FPS
45209 frames in 5.0 seconds = 9041.769 FPS
45261 frames in 5.0 seconds = 9051.820 FPS
45400 frames in 5.0 seconds = 9079.863 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

AND WITH A 1024X768 RESOLUTION
krotaz@Trespatines:~$ glxgears -printfps
43814 frames in 5.0 seconds = 8762.722 FPS
55838 frames in 5.0 seconds = 11167.513 FPS
66783 frames in 5.0 seconds = 13356.490 FPS
79697 frames in 5.0 seconds = 15939.339 FPS
71978 frames in 5.0 seconds = 14395.525 FPS
76382 frames in 5.0 seconds = 15276.309 FPS
63849 frames in 5.0 seconds = 12745.199 FPS
45913 frames in 5.0 seconds = 9182.484 FPS
46128 frames in 5.0 seconds = 9225.443 FPS
46118 frames in 5.0 seconds = 9223.580 FPS
45403 frames in 5.0 seconds = 9080.572 FPS
45209 frames in 5.0 seconds = 9041.769 FPS
45261 frames in 5.0 seconds = 9051.820 FPS
45400 frames in 5.0 seconds = 9079.863 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

As you can see the performance es much lower with the 32 bit OS, why is this?? is this normal?? or do I have to edit something in the xorg.conf file??

By the way my video card is a Gforce 7600gt 256 MB PCI-E

Bye

---

### Post by renzokuken on 2007-02-09
glxgears is not a benchmarking tool so dont read too much into its results. it relies on a whole host of factors other than grafix cards - ram, processor, distro etc

i guess the difference is caused by the extra processing power of 64 bit computing

---

### Post by rich.bradshaw on 2007-02-09
$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
3215 frames in 5.0 seconds = 642.974 FPS
4555 frames in 5.0 seconds = 910.984 FPS
3898 frames in 5.0 seconds = 779.536 FPS
3511 frames in 5.0 seconds = 702.107 FPS
4221 frames in 5.0 seconds = 844.058 FPS


I only get 1000FPS, I though I was super cool :(

---

### Post by goatflyer on 2007-02-09
> **rich.bradshaw said:**
> $ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
3215 frames in 5.0 seconds = 642.974 FPS
4555 frames in 5.0 seconds = 910.984 FPS
3898 frames in 5.0 seconds = 779.536 FPS
3511 frames in 5.0 seconds = 702.107 FPS
4221 frames in 5.0 seconds = 844.058 FPS


I only get 1000FPS, I though I was super cool :(

And if you shrink your glxgears window to a little-little square, you could squeeze 1300 out of it!

---

### Post by krotaz on 2007-02-09
well thanks for your answers at this moment I belive that the poor performance was because I was using the .386 kernel instead of the generic kernel (my processor is a X2 3800+) so this give much better performance.

By the way, is there a tool (benchmarking) for linux that can tell me if my videocard is ok??

Thanks

---

### Post by G Morgan on 2007-02-09
> **rich.bradshaw said:**
> $ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
3215 frames in 5.0 seconds = 642.974 FPS
4555 frames in 5.0 seconds = 910.984 FPS
3898 frames in 5.0 seconds = 779.536 FPS
3511 frames in 5.0 seconds = 702.107 FPS
4221 frames in 5.0 seconds = 844.058 FPS


I only get 1000FPS, I though I was super cool :(

GMA950?

Yeah the frame rates you get out of glxgears are ridiculous.

---

