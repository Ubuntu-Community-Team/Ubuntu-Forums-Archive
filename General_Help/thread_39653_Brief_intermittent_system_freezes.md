---
title: "Brief intermittent system freezes"
date: 2005-06-06
forum: General Help
---

### Post by d0gbert on 2005-06-06
Hello!

I just installed Hoary and am loving it!  However, I am experiencing brief intermittent system freezes.  They only seem to last for a second or two and become more frequent when I am performing more activity (e.g., opening and closing windows, surfing from site to site, etc.).

Some of the symptoms of the freezes are that the mouse cursor will "freeze" momentarily and if I am listening to music or an audio stream the sound will "stutter" a couple of times.

This happens frequently enough to be annoying.

Anyone have any ideas as to the root cause?  If this issue has already been addressed in a thread, please post a link to it, though I did a search and did not find much in the way of positive identification and resolution.

Hoary is installed on a Dell Inspirion 8100, 512MB RAM.  I'm using a Netgear WG511.

Thanks!
D0gbert

---

### Post by doans on 2005-06-06
[QUOTE=d0gbert]Hello!

I just installed Hoary and am loving it!  However, I am experiencing brief intermittent system freezes.  They only seem to last for a second or two and become more frequent when I am performing more activity (e.g., opening and closing windows, surfing from site to site, etc.).

Some of the symptoms of the freezes are that the mouse cursor will "freeze" momentarily and if I am listening to music or an audio stream the sound will "stutter" a couple of times.

This happens frequently enough to be annoying.

Anyone have any ideas as to the root cause?  If this issue has already been addressed in a thread, please post a link to it, though I did a search and did not find much in the way of positive identification and resolution.

Hoary is installed on a Dell Inspirion 8100, 512MB RAM.  I'm using a Netgear WG511.

Thanks!
D0gbert[/QUOTE]
 Are you using a Nvidia graphics card?  I have a Nvidia graphics card and initially had problems with Ubuntu randomly locking up using the generic nv driver.  If you do make sure you use the Nvidia drivers.  Hope this helps.

---

### Post by shakin on 2005-06-06
Open a process viewer like Top so next time this happens you can see if any processes have a spike in CPU usage.

And if the delay is only on graphical parts of the system (eg. sound still plays) then maybe your video driver is incorrect or using a lowly vesa driver. To check your driver run:
```

$ grep -A 10 Section\ \"Device\" /etc/X11/xorg.conf |grep Driver

```

---

### Post by hackeron on 2007-08-31
I'm having the same problem with Gutsy - the system does not lock up, it just freezes intermitently whether X is running or not. Top isn't showing anything out of the ordinary during those brief freezes.

There is no IO wait on the disk or anything like that either but every so often, 10-15 times a day, the system freezes for 2-5 seconds and unfreezes.

---

### Post by nathanhillinbl on 2007-10-22
I'm having this exact same problem, I'm using the free nvidia drivers (the ones that came automatically installed) and are kind of ticked that I have to stop once every 5 mins for about 10-15 seconds, sometimes as long as 30 seconds at a time. Cuts down just a little on productivity....

Any help would be greatly appreciated.

Thanks,
--Nate

---

### Post by hackeron on 2007-10-22
My problem turned out to be the kernel I was using. I accidentally removes linux-general with linux-rt (realtime) -- going back to general or i386 fixed the problem.

---

### Post by utkjamie on 2007-11-07
This problem has been driving me nuts over the past few weeks. Every 3-4 seconds the system freezes for a split-second and then resumes. Most of the time I don't notice it because the freezes are so brief. However, it becomes very apparent when trying to type something like an email or an article I'm writing and nothing comes out. (Imagine being able to finish typing a word every 3-4 seconds!) It's also apparent when watching video; the video will freeze every 3-4 seconds.

I'm running the 2.6.22-14-generic kernel and ATI Radeon video drivers. Nothing in my Process List spikes during these freezes, so it doesn't appear to be any specific app. I removed Compiz a few weeks ago, thinking that was the culprit.

I'm desperate for a solution because this is really starting to cut into my productivity.

---

### Post by utkjamie on 2007-11-19
I thought I had the problem fixed by tweaking my video card settings in xorg.conf but now the freezing is back with a vengeance, leaving me unsure of what the cause is. I don't have any CPU-hogging apps running, so I'm at a loss to understand what's going on. CPU policy is set to Performance to prevent stepping down to 600 MHz. Even typing this message is being met with split-second pauses every few seconds, making it difficult to even write a few sentences.

---

