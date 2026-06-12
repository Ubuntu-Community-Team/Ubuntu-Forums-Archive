---
title: "ubuntu very slow"
date: 2008-03-05
forum: General Help
---

### Post by jayhay on 2008-03-05
Hello everyone,

I am relatively new to Ubuntu and to Linux in general but I seem to be having problems. I have recently installed Ubuntu Gutsy and am really impressed with the operating system. But it seems to run very slowly, My system is:

2GHz Intel Celeron
1.5GB Kingston RAM
256MB nVidia GeForce LX750 (or something)
Foxconn motherboard
200GB Maxtor HDD

I have installed the latest nVidia drivers, and the advanced desktop effects work like a charm. But just generally, everything seems to take long time to load, and the response time with keypresses, or events seems to be very long. Also, the hard drive seems to be permanently working, I can hear it ticking over constantly (there is no hard drive light on my machine). 

I have the system monitor applet running on the bottom panel, and it seems to indicate that the CPU is always working at almost 100%, but when I open the gnome system monitor, then no more than about 30% of the CPU is in use, including the system monitor itself taking up 12%. 

It is very frustrating, as I feel like this operating system has a lot to offer, but I am continually waiting for it... does anyone have any suggestions?

---

### Post by chewit on 2008-03-05
Lookingat your specs, Kingston RAM is not the best RAM. Usually bad hardware can be a problem. I also have cheap RAM, but mine pc is fast.

But usually, cheap ram is not going to give u get performance.

---

### Post by MultipleSargasms on 2008-03-05
> **chewit said:**
> Lookingat your specs, Kingston RAM is not the best RAM. Usually bad hardware can be a problem. I also have cheap RAM, but mine pc is fast.

But usually, cheap ram is not going to give u get performance.

I was always under the assumption that Kingston ram is actually pretty good. You're pretty safe when you buy from any one of the leading competitors like Kingston/Crucial/Patriot/Corsair. Just make sure you get the correct ram for your particular system

---

### Post by knutschr on 2008-03-05
Can you
```
top
```
and give the resault here?

---

### Post by myoungf1 on 2008-03-07
I am having the same problem on my Kubuntu 7.10 installation.  I load up kubuntu and it just seems sluggish.  I go back to Windows and my computer just flies.  Would like to see if others are having the same problem with there K/Ubuntu 7.10 install

---

### Post by nlong on 2008-03-07
I have had a similar problem on a couple different machines and a different video driver fixed both issues.  If you haven't already done so, I would install envy and let it update your video driver.  If that doesn't help, try the restricted driver.  I certainly wouldn't blame the memory, Kingston or otherwise.  Cheap/bad ram typically either works, or doesn't, and 1.5Gbs should be plenty to run Ubuntu with those specs.

---

### Post by myoungf1 on 2008-03-07
> **nlong said:**
> I have had a similar problem on a couple different machines and a different video driver fixed both issues.  If you haven't already done so, I would install envy and let it update your video driver.  If that doesn't help, try the restricted driver.  I certainly wouldn't blame the memory, Kingston or otherwise.  Cheap/bad ram typically either works, or doesn't, and 1.5Gbs should be plenty to run Ubuntu with those specs.

Thanks for the info but I am already using the latest ati restricted drivers from the ati website, I think its 8.2 something.

---

### Post by myoungf1 on 2008-03-25
Just wondering if anyone has tried to upgrade to hardy heron beta and seen if hardy fixes this slow down problem or not.

---

### Post by Therion on 2008-03-25
```
sudo aptitude install bootchart
```

Then reboot.  Once you've logged in, look under ~/var/log/bootchart and post the image you have there.  The graph will give a good indicator or whats going on when you start your PC and possibly show what's causing the slowdown.

It will keep putting new bootcharts there every time you reboot, however, so if you want to stop it then uninstall bootchart.
> **myoungf1 said:**
> Just wondering if anyone has tried to upgrade to hardy heron beta and seen if hardy fixes this slow down problem or not.
I did and I found that most things were pretty snappy with Hardy, even off the LiveCD.  Hard drive install was great (Firefox was downright *scary* fast); everything seemed very quick to load, launch, etc., but then I don't have any complaints about speed on my system to begin with.

---

