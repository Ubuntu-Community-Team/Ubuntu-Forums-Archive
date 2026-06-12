---
title: "Laptop's resolution stuck in 1024x768 and decreased performance"
date: 2013-06-05
forum: General Help
---

### Post by SangeetKhatri on 2013-06-05
I don't know what happened but my laptop's resolution is not stuck in 1024x768 even though the laptop's resolution is 1366x768. Another problem i am facing is that the performance of my PC all of a sudden decreased. The animations that were fluid smooth before now take a very long time. And everything seems slowed down.

Worse thing is that a 4:3 aspect ratio resolution is stretched in a 16:9 widescreen panel hence making everything appear look wider. Please help me as using my laptop is a pain in the A$$ for now.



My "xrandr" output is 

```
 sangeet@sangeet-Aspire-5738:~$ xrandrxrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 

```

And also in the "Monitor Settings" app there are no other resolutions available. The only two options i seem to find are 1024x768 the Auto option. None of which can solve my problem.

Any help would be highly appreciated.
Thank You

---

### Post by TenPlus1 on 2013-06-05
If your laptop has Ati or Nvidia graphics be sure to install binary drivers to help with playback lag and correct resolutions...

---

### Post by SangeetKhatri on 2013-06-05
It has Intel Integrated graphics, so naturally i re installed the Intel drivers but they do not seem to solve the problem at all.
It is still the same. Also did i mention that animations and other graphics related stuffs are crappy as well..

---

### Post by hal8000 on 2013-06-05
Post the output of these commands:

```
inxi -G

lspci | grep -i vga
```


If inxi is not installed, install with sudo apt-get install inxi
Looks like the Intel driver is not installed. It may be the i915
driver but without knowing chipset its only a guess.

---

### Post by SangeetKhatri on 2013-06-05
This thread is solved. I planned to reinstall lubuntu as there were a lot problems in it and after the reinstall everything seems to work fine as it should. So this thread is closed and i wiil mark it as [SOLVED]
Thankyou guys for your precious time.
:D

---

