---
title: "Unity locked up"
date: 2013-12-07
forum: General Help
---

### Post by jason13 on 2013-12-07
After I restarted my computer because of a browser lock up I am unable to do anything on my desktop. The items on the top bar still work (wi-fi, volume) but none of the icons are working. I can't open browsers or a terminal or the file system. I've restarted twice and it boots fine but the desktop is locked. What should I do?

---

### Post by heir4c on 2013-12-07
What happen in your browser? What you mean with "browser lock up"?

---

### Post by jason13 on 2013-12-07
When my memory is near capacity (most of it taken by browsers) it will either slow down until I can close tabs or stop responding and I need to restart.

---

### Post by heir4c on 2013-12-07
How much memory you have? And have you a swap partition? Maybe more about your hardware (graphics card, cpu)
And how you see that your memory is near capacity? with the command top ? Or via system monitor? ....

---

### Post by jason13 on 2013-12-07
I have 2 GB memory with a 4 GB swap partition on the same device my OS is on, with an nvidia 660 GE video card. I let the system monitor run in the background in order to more easily kill processes that may be requiring memory. As of now I can't even do that, but like I said, some menus are visible but visible only, none of the menu items currently work.

---

### Post by heir4c on 2013-12-07
maybe you can reset Unity. Here a link that maybe help: [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)
Have you 12.04 or a later version. In the link there mentioned about 13.04 and 13.10.

---

### Post by jason13 on 2013-12-07
I'm using 12.04

---

### Post by heir4c on 2013-12-07
Than you can try to use:
```
unity --reset
```
Maybe you need to be root so use than sudo in front of the command above.

---

### Post by tgalati4 on 2013-12-07
Check the SMART status of your hard drive.  If you have disk errors, that can cause a lot of problems.  If your browser cache file is too big, that will cause slow performance--try clearing it.

---

### Post by jason13 on 2013-12-08
I tried to get into the drive from my thumb drive installation of ubuntu and once I reached the desktop I ran into the same problem. the desktop loads, the menus display but the icons don't do anything. I reseated the memory sticks thinking that might be it but to no effect. because it happened on the HD installation and the thumb drive installation it makes me think it's not the HDD but another hardware problem. at this point I'm pretty lost as to what to try next.

edit: about one day prior to this problem I was having problems with updates, it would repeatedly fail on an authorized source error.

edit 2: my desktop has an installation of Windows 7 on a separate hard drive and I tried booting to that and ran into a very similar problem, the desktop and immediately accessible menus are available but programs and windows won't load. definitely makes me think it's a hardware error, but what piece of hardware.

---

