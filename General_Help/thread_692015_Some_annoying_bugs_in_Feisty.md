---
title: "Some annoying bugs in Feisty"
date: 2008-02-09
forum: General Help
---

### Post by jms1989 on 2008-02-09
Hello,

Here lately, I've been experiencing some annoying problems.

One is that the applications take longer then they should to load. I mean, when I open a app or file, the HDD Light won't start blinking until it has some activity about 2 or 3 seconds after I open something. Sometimes longer. It should load right when I open the app.

Second, firefox sometimes craps out on me when things get tough for it. Today, I was at a website that uses some heavy javascript and it kept hiccuping.

Third, Linux is not registering all of my installed memory. Windows registers almost all of it. I have two Samsung 512MB PC2700 DDR. Right now it's registering only 1010MB when the BIOS sees 1024MB. The memory is not being shared by anything. All of it goes to the OS.

I've been using Ubuntu for at least a year and a half and I don't mind using the terminal if I have to but I prefer the GUI because I can remember images better then just words, most of the time.

I might end up post more bugs when I come across them, until then, help me solve my bugs I have now.

Thanks,
jms1989

---

### Post by jms1989 on 2008-02-12
Nobody has a simple answer? :(

I recently tried to reinstall ubuntu but I kept having trouble getting the NVIDIA drivers to install and actually work. The X Server kept crashing with I installed it, odd, it works on my older install but not on a new one. I also can't get a resolution higher then 1024*768 when my max sould be 1280*1024, where I like it.

The apps are still a little slow when first executed but once loaded in memory, they work fine. I just don't understand why they are slow to load, like there is a delay before the hard drive actually does something.

Will somebody please help me?

---

### Post by karellen on 2008-02-12
I don't know about the ram problem, but it's not that uncommon. I have 512 mb ddram and sometimes I was told I'm having 511 mb or 510 mb of ram, so I guess it depends :D.
and for the bugs in feisty, maybe you should try to do a clean install of gutsy. it works well for me (but anyway feisty was ok too, I have a pretty old rig). firefox sometimes freezes, but I got used to it. gutsy has a more solid x server and maybe that would help you with your video card problems
I also found this nice tool, ubuntu-tweak, for customizing your Ubuntu: more about it here: [http://www.ubuntugeek.com/howto-tweak-ubuntu.html](http://www.ubuntugeek.com/howto-tweak-ubuntu.html)
for general tweaks: [http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)
[http://cybernetnews.com/2006/06/07/tweak-ubuntu-to-maximize-performance/](http://cybernetnews.com/2006/06/07/tweak-ubuntu-to-maximize-performance/)
hope it helps a little
cheers :)

---

### Post by jms1989 on 2008-02-12
I'll try that. Gusty seems to be more compatible with my AGP Video card, I think I'll try it later on this week.

---

### Post by Kevuntu on 2008-03-06
I know what you mean. I have the same problem. I tried nearly everything and I'm running out of ideas. I noticed you're using an ATA100 IDE Hard Drive. Well, so do I and the problem seems to be coming from there.

Try the following command (close all programs first):
```
sudo hdparm -tT /dev/sda
```
This shows your hard drive speed.

Here are my results:
> Timing cached reads: about 170 MB/sec
Timing buffered disk reads: about 7 MB/sec

These numbers should be a LOT higher (like 10 times) and it's possible:
```
sudo hdparm -c 1 -d 1 /dev/sda
```
This will set your IO_support flag to 32 bit and turn on DMA to speedup the HDD.

Unfortunately here's what it gave me:
> setting 32-bit IO_suport flag to 1
HDIO_SET_32BIT failed: Invalid argument
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Inaproptiate ioctl for device
IO_support = 0 (default 16-bit)

That means I have to wait 30 seconds for firefox to load, opening terminal takes 10 seconds, and I'm forced to use lighter alternatives like Xfce (and still it feels too slow) because gnome login was taking about 3 minutes and even opening gnome's menu was slow (about 5 seconds every time). I know that I only have 240MB of memory and a Pentium 3 processor, but that's not so bad! Well, I guess I'll have to find lighter distros.

---

