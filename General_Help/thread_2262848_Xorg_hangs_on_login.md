---
title: "Xorg hangs on login"
date: 2015-01-27
forum: General Help
---

### Post by blackbird34 on 2015-01-27
Hi all. I have a Lenovo Z50-70 (Intel i5-4210U, hybrid graphics with the intel integrated one and a NVidia Geforce 820M card too)

I think i'm having problems with my graphics drivers. When i boot Ubuntu the login screen does not show up, I merely get a blank, black screen, although if i type  my password in, Ubuntu logs in and reacts to typed commands (i use synapse to launch everything). I can also tell parts of the system are running as the little lights showing that my caps lock and num lock are on still work. And I can log into a tty normally. 

So i think this must be Xorg or some portion of the graphics stack getting stuck. I installed proprietary drivers from the Additional Drivers utility too but i think i may have got the wrong  ones (since installing the nvidia-340 package i have encountered advice [here]("http://askubuntu.com/questions/518985/ubuntu-14-04-and-nvidia-geforce-840m-compatability-on-64-bit-laptop/557395#557395") saying i should specifically use that version - they are talking about the 840M that is very close to the 820M)

It also is very unreliable waking from suspend, sometimes it freezes (requiring Alt+SysRq R-E-I-S-U-B), sometimes  it doesn't. 

I really miss Ubuntu.

---

### Post by Bashing-om on 2015-01-27
blackbird34; Hello;

I often see 'nvidia-prime' recommended for hybrid Intel/Nvidia .
> 
Description-en: Tools to enable NVIDIA's Prime
 This is a set of tools which will enable
 NVIDIA's Prime on MUXless systems.


[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

