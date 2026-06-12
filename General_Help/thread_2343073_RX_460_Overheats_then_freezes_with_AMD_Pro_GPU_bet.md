---
title: "RX 460 Overheats then freezes with AMD Pro GPU beta Linux"
date: 2016-11-12
forum: General Help
---

### Post by cgameing on 2016-11-12
I got 2 gpus and two Ubuntu installations right now. My r7-240 (ubuntu 15.10 with fglrx drivers) and xfx rx-460 (ubuntu 16.10 with new drivers).

I would like to use my new gpu to play games as its 3x better then my current one. But I cant as it freezes after a while, here is how I came to that conclusion.

1) I installed 16.04 and then updated to 16.10 installed steam and the new amd drivers.
2) Installed a few games (csgo, tf2, binding of issac)
3) Found after a while the games freeze
4) When the games froze the gpu was surprisingly hot.
5) Found the higher the settings the quicker the game froze.
6) Restarting the computer made the freeze occur quicker then before.

So clearly my gpu is running hot and its freezing to prevent breaking or something?
Is there anyway I can fix this, like underclocking it or something else?
I assume im one of the few people with this issue.

*edit* There are no open drivers for this gpu, and when there is no driver installed steam wont start
*edit* Gpu may not be overheating as it only goes up to 53 Degrees celcius (125.6 farenheit)

Thanks for any help.
Have a great day.

---

### Post by QIII on 2016-11-12
Hello!

What happens when you install AMDGPU-PRO?

I'm not sure it will help, since it's just AMDGPU with the proprietary overlay, but it's worth a try.

To be sure if it is actually running hot, run

```
sensors amdgpu-pci-0100 | grep temp1: | cut -c15-23
```

You may also want to check the GPU activity with 

```
sudo cat /sys/kernel/debug/dri/64/amdgpu_pm_info | grep GPU | cut -c13-17
```

---

### Post by alexjpowell on 2016-11-12
Can you please take a photo of the inside of the case, in a matter where we can see the position of the GPU and the position of the fans?

---

### Post by cgameing on 2016-11-13
There are no open source drivers for this gpu, sorry for the mistake in the question.

There are 2 case fans, and plenty of room for the gpu to breathe, Its not a overkill rig and the only way thing that would make a difference at this point is watercooling.

---

### Post by alexjpowell on 2016-11-13
It may have two case fans and plenty of room but it's the way the air circulates that matters
It would also be a problem with the PSU supplying dirty electricity

---

### Post by cgameing on 2016-11-13
Both case fans are pulling out, and the gpu is sucking air from the bottom and not effecting the case, also I didn't bother pluging in the gpu, because this was just temporary to show what it would look like. Im currently using my old gpu instead.[ATTACH=CONFIG]272109[/ATTACH]

---

