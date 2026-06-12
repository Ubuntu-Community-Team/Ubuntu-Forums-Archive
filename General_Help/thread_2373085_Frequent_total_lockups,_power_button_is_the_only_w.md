---
title: "Frequent total lockups, power button is the only way I can find to recover"
date: 2017-10-02
forum: General Help
---

### Post by brian666 on 2017-10-02
I'm running Ubuntu Studio 16 LTS, XFCE desktop, all patches applied, on an AMD Phenom II x6 with 8GB of RAM. In the last 3 weeks or so (I can't tie it down to any specific event) the PC has started locking solid at regular and frequent intervals. Again, I can't tie it down to using any particular application (although playing a video in VLC will reliably lock things up in less than half an hour), I've even had a couple of occasions where everything locked solid as soon as the desktop appeared, and once before I'd even started the GUI (the PC boots to the command prompt). 

To start with, the PC was using the onboard graphics, and it was noticeable that each time it locked up, I got a sort of pixellated second cursor to one side or the other (variable, but never both at once). I wondered about the onboard graphics chip, so I put a cheap graphics card (GeForce 8400 GS) into the PC. This did seem to improve things, to the extent that I thought it had fixed the problem, but no, it soon came back. The only lasting effect of the graphics card is that the pixellated second cursor no longer appears. 

When the lockup happens, absolutely nothing works, the cursor stays put, my only way out is the power button. It is noticeable that, if I'm playing a video, the sound continues as a steady tone. 

It was suggested that I try a genuine NVidia driver. I downloaded the appropriate one from their website, but that had no effect. 

Before switching to Ubuntu Studio, I used to use Debian, so I tried booting from a Debian 9 live DVD and then playing a video again. Well, it did improve things, this time it took about 90 minutes before everything locked solid again. There's no corruption of the screen, BTW, it's just like the video morphed into a still photo. 

I've tried looking at the system logs, but at least to my definitely non-expert eye, I can see nothing untoward, no mention of any errors. 

I've also tried keeping an eye on the sensors, there doesn't seem to be any CPU overheating, and there's plenty of unused memory. 

And that's as far as I've been able to get. Does anybody have any ideas, please, because it's driving me crazy. 

Thanks, 

Brian.

---

### Post by ian-weisser on 2017-10-02
Any clues in /var/log/syslog around the time of a freeze?

---

### Post by DuckHook on 2017-10-02
Welcome to the forums, brian666:

Since two different OSes led to the same results, my guess is that the problem is almost certainly something to do with your HW. The only other test would be a completely different OS like Windows (to rule out something really basic like the kernel or a shared driver), but I'm guessing that you are not eager to load Windows on this box just for fun.

The Phenom II line isn't really that old, so I'm guessing that your box is not that old either. However, MOBOs can develop cracks or thermal component failures. They are incredibly hard to diagnose. Basic HW failures are not likely to register in your logs.

You could try the following:

[LIST=1]
[*]Run a memory check. The problem could be a failing RAM module.
[*]Stick a real thermometer on the CPU. Sometimes, lm-sensors does not return reliable data.
[*]Make sure that all RAM is properly seated.
[*]Apply *light* pressure—make sure it's light—to the MOBO to check for cracks. Flexing the MOBO this way will sometimes show you where the crack is, often by sound rather than sight.
[*]Check for signs of burned or incomplete soldering on the MOBO.
[/LIST]
Aside from the above, not sure how much more help I can be.

---

### Post by brian666 on 2017-10-03
Ian: No, I checked all of the old logfiles after rebooting, at least to my eye there was no indication of any problems. 

DuckHook: (know your namesake well!) OK, thanks for the hints, I will give this lot a try. Depending on cost, I was going to try swapping out the 8GB module (the system will take two of them if it doesn't fix the problem) and I also have a larger fan to put in there if the CPU is overheating (I don't think so, but I guess it's possible), HandBrake gives a multi-core a fair bit of exercise. :) The system is about 3 years old, BTW. You are dead right about Windows, the latest version I have to install is from when I retired, which means Windows XP. :) I ditched Windows as soon as it stopped earning me a living...

---

### Post by brian666 on 2017-12-12
I forgot about posting the eventual solution to all this, sorry. :( I went round and round in circles for a while longer until I just gave up and bought a new barebones PC, cannibalised the old one and everything worked just fine. I suspect that the problem with the old PC is actually with a failing power supply, and I have a new PSU to try when I get one of those round tuits...

---

