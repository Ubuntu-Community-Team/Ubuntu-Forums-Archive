---
title: "ATI Driver forces 75Hz Refresh Rate"
date: 2007-03-31
forum: General Help
---

### Post by Majorix on 2007-03-31
Hi to all Ubuntu-lovers!

I have this problem bugging me since the time I installed Linux.

The thing is that I can install the driver and then run the initial config to write to the xorg.conf file.

All goes very well upto this point. But when I restart, before X starts, I get a black screen, with a note from my monitor saying "75K, 59Hz" is not supported.

I am 100% sure 75KHz horizontal refresh rate is not supported by my old monitor (59 vertical is, thats not a problem).

I can start X back again by replacing the changed conf file with the original file using the saving mode which doesn't start X.



Now I am asking if there is a way to stop the ATI drivers from force running the monitor on 75KHz.

If anybody knows any kind of a thought that can help, may they feel free to post it.



Thanks for all your help beforehand,
Majorix

---

### Post by mrmonday on 2007-03-31
How did you install the drivers? Do they automatically configure X?

Is what your saying you can boot without the drivers, but get an error with them?

Sorry for all the questions.

---

### Post by Majorix on 2007-03-31
Thing is I tried this in 2 different distros, in different ways, with the same result.

On Ubuntu, I have downloaded the ATI Radeon driver for my video card (ATI Radeon X800) from their official site and installed it without modifying the file in any way. Then I ran aticonfig --initial which modified the xorg.conf (it automatically made a backup too). Finally I restarted the computer, to boot into that error screen instead of X. To recover, I started the computer in console mode, and replaced the modified xorg.conf with the unmodified backup. Starting X worked now.

On Debian, the drivers were in the repos so I installed from there, ran aticonfig --initial, restarted, and got into that error screen again. Since there was no recovery mode in Debian, I had to format that harddisk and that made me mad.

I hope this clears things up.

---

### Post by jocko on 2007-03-31
The few times I've used "aticonfig --initial" to set up xorg.conf it has only managed to mess things up.
Instead of using "aticonfig --initial" to change xorg.conf, try to do it like this:
type this in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
Make sure you select fglrx in the first screen, accept the default on the rest of the questions until you come to the parts concerning the monitor.
Select advanced and make sure to enter vertical and horizontal sync ranges that you know your monitor can handle and select only resolutions that it supports
(try to find the specs for your monitor if you are not sure). After that everything should work.

---

### Post by Majorix on 2007-03-31
Alright thanks for the suggestion, I will try it now and let you know.

---

### Post by Majorix on 2007-03-31
Wow thanks mate it worked, you rock!

Shame on ati for creating such a buggy config tool.

---

