---
title: "Slugish performance at some point"
date: 2013-06-04
forum: General Help
---

### Post by afonteijn on 2013-06-04
Over the last year I have noticed that my PC is snappy with Gnome-shell until a certain amount. After that the user interface get slugish (scrolling down windows, going to the "Activities" overview, switching between windows etc.) 

Normally, I've got some programs open, but nothing that warrants this behavior. For example: currently I've got Firefox open (12 tabs), Chromium (1 tab), Nautilus, the System Monitor and Filezilla. The interesting thing is that i have got lots of free memory (currently 5gb) and the CPU's aren't very busy (20%-30%). Firefox uses most (between 5-10%) 

I have the idea that it is related to the interface. Processes that are not related to the desktop environment still work fine (i.e. Handbrake will encode on full speed). So, I'm wondering if this is related to the video driver. I currently have an Nvidia video card (proprietary drivers installed), however, I had the same problem with my older ATI card (open source drivers).

My current PC is an:
Phenom II X4 3ghz
8Gb memory
Geforce 8600GTS 1gb
I'm currently running Ubuntu 13.04 with Gnome-shell installed on top. However I had the same problem with Gnome-Ubuntu (remix) and with earlier Ubuntu versions. Gnome-shell version is 3.6.3.1

Any help getting my system feeling snappy with multiple programs running is greatly appreciated!

---

### Post by afonteijn on 2013-06-20
Additional information:
This week I upgraded my video card to a Geforce 260 GTX (I got a really good deal on craigslist). I also updated from gnome-shell 3.6 to 3.8. Since then, I have not had any problems with sluggish performance after some point. I noticed, however, that gnome-shell uses 44% of the video memory. The video card has 896 MB of memory and 394 MB is being used. My last card had only 128 MB memory. Could this be the problem? Does Gnome-shell just use an unusual (for me) amount of video memory? Is there a video memory leak? It would explain why my system became slugish before.

---

### Post by afonteijn on 2013-06-21
Correction:
My last card had 512 MB, however I notice in the NVIDIA X Server Settings that the memory of my current card sometimes is used for more than 512 MB. Anyway, I still be interested to know if anyone knows about a nVidia specific memory leak or similar problems and how to solve it.

---

### Post by afonteijn on 2013-07-10
It's a little lonely on this forum. However, just for those who are interested I'll keep you posted of my progress.

I think I was on the wrong track. It doesn't seem to be the video card, but something that has to do with gnome-shell. When I start it up it's size is less than 200mb and then over a period of about 24 hours it grows up to 2gb. The system becomes slugish. I then terminate gnome-shell and restart it, and the system becomes responsive again. I upgraded to gnome-shell 3.8 (which is a great improvement overall) but the memory leak still seems to be there.

If anyone knows of a more permanent solution than just restarting gnome-shell every 24 hours, please let me know!

---

### Post by montag dp on 2013-07-10
Hm, I'm not sure. After 2+ days my whole system (64 bit) is a little under 1 GB with "nothing" open.  I think when I first boot up it's in the 600 - 700 MB range.  Are you saying the gnome-shell process itself is at 2 GB after 24 hours?  Mine is at 265 MB at this point (after 2+ days).

---

### Post by afonteijn on 2013-07-11
Thanks for your response! Yes, in the system monitor gnome-shell starts out with a size around 150mb. Just had to do a restart again because gnome-shell grew from 400mb to 1,1gb in a matter of minutes. I have had it go over 2gb. I'm also running the 64 bit version. 

It might be that an extension or program is triggering this behavior. I'll disable the extensions and see if that changes anything.

---

### Post by AMDri on 2013-08-07
This will probably be my last update. Since I have cut down on the extensions, I haven't had any memory leak problems anymore. I haven't figured out which of the extensions was the problem. So, for anyone who might visit this thread in the future and has a similar problem: disable all your extensions and turn one at the time on and see what happens. It is a bit of an art! :)

---

### Post by jonijones on 2013-09-27
I was having the same issue and disabling all extensions solved it.
Anyways, I've narrowed it down to the "sensors"-extension which displays the lm-sensors values.

---

