---
title: "Blank brown desktop after login on feisty (desktop missing)"
date: 2007-09-04
forum: General Help
---

### Post by seaborn on 2007-09-04
Hi,

   I installed feisty on my new laptop a few days ago (thinkpad x61), and I had everything working great for about two days (compiz was running, wireless, it was playing DVDs, fingerprint scanner) all from the gnome desktop I had configured. I had turned the laptop on and off on several occasions, all with a successful login, and succesfful desktop setup.

   I restarted my computer last night and although everything goes fine (the login screen is normal) once I have had a successful login, all I see is a brown screen with a cursor and part of a grey window in the top left. When I curse over the grey window my cursor changes to the typing icon (looks like an 'I').

   If I login via failsafe terminal, I can run all of my programs from the command line, but every time I try to login to my gnome desktop I get the above problem.

   I also tried browsing previous posts about issues similar to mine, but none of them helped to solve the issue. 

   I was wondering what I should do to get my desktop back - although I was enjoying it I'm not that experienced using ubuntu yet. I would really like to be able to get my desktop back without redoing ubuntu altogether. 

Thanks very much for your help!

---

### Post by be4truth on 2007-09-04
This could be related to the latest kernel update. Did you run an update 2-3 days ago? If so you should have an older and a newer kernel in your GRUB menu (the higher number is the newer kernel). Try the older kernel and see if this one works. There seem to be problems with some graphic settings being broken with the new kernel.

---

### Post by seaborn on 2007-09-04
Hi, thanks for the quick reply.

I tried booting up in the old kernel (2.6.20-15-generic #2) and  I got 

intel(0): failed to allocate framebuffer. Is your VideoRAM set too low?

four times. It then said

intel(0): Couldn't allocate video memory.

Is there anything else you think it might be?

Thanks again for your help

---

### Post by be4truth on 2007-09-04
You could boot into recovery mode and type 

```
dpkg-reconfigure xserver-xorg
```

This will launch a wizard that leads you through the configuration of your xserver (graphic card). If you can't answer a question go with the defaults. Your present xconfig file will be saved as a backup with the date and time.
After that reboot and see.

---

### Post by seaborn on 2007-09-04
I tried the new kernel again and after he black screen with the Ubuntu logo and the loading bar it just goes to black screen.

It wouldn't be the end of the world if I had to reconfigure my desktop, but I was hoping that at least I could save all of the programs I have installed (if it ends up not being possible to get my desktop configuration back).

---

### Post by be4truth on 2007-09-04
This could also be a gdm (Gnome Desktop Manager) login problem but I can't help here. Look around in the forum for this threads. Just look a bit around. Don't be too hasty. Help is there. To reinstall is the last option.

---

### Post by seaborn on 2007-09-04
Ok I went through the entire configuration setup and went to login again, but had the same issue as the beginning. How frustrating!

Thanks anyway

---

### Post by be4truth on 2007-09-04
> **seaborn said:**
> Hi, thanks for the quick reply.

I tried booting up in the old kernel (2.6.20-15-generic #2) and  I got 

intel(0): failed to allocate framebuffer. Is your VideoRAM set too low?

four times. It then said

intel(0): Couldn't allocate video memory.

Is there anything else you think it might be?

Thanks again for your help

Did you allocate video memory in the configuration?

---

### Post by seaborn on 2007-09-04
Yes I did,

Graphics Subsystem
Graphics chipset : 	Intel Graphics Media Accelerator X3100
Video memory : 	Up to 256 MB
Video memory type : 	DVMT
Graphics bus interface :	PCI Express

I gave it 256MB

---

### Post by seaborn on 2007-09-04
I think I'm just going to re-install and be a bit more careful next time, who knows maybe I'll learn something new.

---

