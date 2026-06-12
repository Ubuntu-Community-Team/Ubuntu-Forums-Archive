---
title: "Nvidia and Performance, Help!!!"
date: 2007-04-07
forum: General Help
---

### Post by HostMyPort on 2007-04-07
Hi, im new to linux and so far for this 7 months everything has being working as a dream i don't have any problems or whatsoever, im using Ubuntu  anyways on this days i wanted  to start messing around with my video card NVIDIA Geforce 6200 AGP8x 256MB i also installed Cedega (i love gaming and said let's give it a try on linux) i went with the installation of NFSU everything went good, but when i start playing it seems to be very slow the graphics look nice but  from time to time it gets slower then faster (like a slideshow to be more specific) then i started looking on the net what could be the problem and i was somethings about the Pixel shader or motion blur that has to be set  someway on the Cedega (didn't work) but anyways the game still goes slow for some reason.

I think that it could be some bad settings on my video card:

i used this to see the frames per seconds that my cards is working on (glxgears -info) and this is what i get :

4900 frames in 5.0 seconds = 979.917 FPS
4573 frames in 5.0 seconds = 914.574 FPS
4893 frames in 5.0 seconds = 978.502 FPS
4820 frames in 5.0 seconds = 963.943 FPS
4498 frames in 5.0 seconds = 898.096 FPS
3309 frames in 5.0 seconds = 661.729 FPS:confused: 
2949 frames in 5.0 seconds = 589.797 FPS:confused: 
3859 frames in 5.1 seconds = 755.881 FPS
3973 frames in 5.0 seconds = 789.800 FPS
4410 frames in 5.0 seconds = 881.939 FPS
4525 frames in 5.1 seconds = 893.485 FPS
4546 frames in 5.0 seconds = 908.802 FPS
4772 frames in 5.0 seconds = 946.495 FPS
4526 frames in 5.0 seconds = 904.938 FPS

and so on, as it can be seeing there is an irregularity there and i have tried messing around with the nvidia settings and got it to work better:

6928 frames in 5.0 seconds = 1385.488 FPS
6994 frames in 5.0 seconds = 1398.734 FPS
7003 frames in 5.0 seconds = 1400.456 FPS
7005 frames in 5.0 seconds = 1400.334 FPS
6994 frames in 5.0 seconds = 1398.757 FPS
6977 frames in 5.0 seconds = 1395.271 FPS
6999 frames in 5.0 seconds = 1399.635 FPS
6992 frames in 5.0 seconds = 1398.231 FPS
7011 frames in 5.0 seconds = 1402.132 FPS
7008 frames in 5.0 seconds = 1401.450 FPS
6335 frames in 5.0 seconds = 1266.949 FPS:confused: 
6336 frames in 5.0 seconds = 1267.081 FPS:confused: 
6784 frames in 5.0 seconds = 1356.722 FPS
6989 frames in 5.0 seconds = 1397.716 FPS
6994 frames in 5.0 seconds = 1398.771 FPS

but i see that still is a irregularity i actually don't know which one is better the first one or the second one, could this be affecting the game or it could be something else here are the specs of my box:

Computer
Processor	Intel(R) Celeron(R) CPU 2.66GHz
Memory	516MB (358MB used)
Operating System	Ubuntu 6.10

Display
Resolution	1024x768 pixels
OpenGL Renderer	GeForce 6200/AGP/SSE2
X11 Vendor	The X.Org Foundation

if you guys could help me set it up or tell me what to do if i need to change something to improve those bottlenecks i will really appreciate it, like i said i really like ubuntu it's very stable and i have left my pc running for almost a week and it was like nothing happened my system is more stable and more responsive i am really using my machine now. It rocks :guitar: 

peter.

---

### Post by Paul41 on 2007-04-12
Are you using the default video drivers or did you install the nvidia drivers? If you haven't installed the nivida driver that could be your problem.

---

