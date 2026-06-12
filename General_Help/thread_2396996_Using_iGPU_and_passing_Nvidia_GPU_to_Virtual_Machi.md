---
title: "Using iGPU and passing Nvidia GPU to Virtual Machine running Windows"
date: 2018-07-24
forum: General Help
---

### Post by marovargovcik on 2018-07-24
Hey guys,

this is a long shot question. Sorry about it.

I am Mac user but Apple no longer feels like worth paying more (I really liked operating system but it's no longer true). 
So i decided to get rid of all Apple products and build a PC (Intel + Nvidia because of better Linux support overall) with Ubuntu. 
I have not bought any parts of the PC yet.

I really can't work on Windows because of lack of terminal (I am frontend web developer) but I like to play games occasionally. 
Dual boot is the easiest workaround but it is not really "comfy" solution because I have to shutdown Ubuntu and boot into Windows therefore disconnecting from FTPs/SSH saving and pushing code to git. I can't just say "whatever, let's play some games" without quitting my IDE, text editors so that's one big minus.

I was thinking if it's possible to have Ubuntu running on iGPU (Intel HD) and passing GPU to VM running Windows. 
It has a huge benefit I can think of:
- GPU is not running most of the time (power efficiency, theoretically extending lifespan of GPU)

I don't expect a complete walkthrough of setup as answer to my question but what I am expecting is:
1. Is it possible to do such a thing?
2. If yes, how about gaming performance in games? Is it a lot worse than running Windows "classic" style?

Any useful links, where I can read more about it, are welcome. 

Thanks for reading, have a nice day.

---

### Post by TheFu on 2018-07-24
Yes. It is usually called PCI passthru.
Yes. 95% of native, assuming the hostOS isn't too busy.
The virtualization subforum here has lots of links.

The required hardware is picky to make it happen.  Generally, higher end GPUs are needed, so don't expect a $150 GPU to be supported.

BTW, you shouldn't use plain FTP since the 1990s. Use sftp, please.

---

