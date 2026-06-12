---
title: "Going nuts: white noise plays through over music whenever I compile code"
date: 2021-02-14
forum: General Help
---

### Post by belnac on 2021-02-14
I'm on the verge of going nuts! I've got the weirdest issue that I'm hoping the community can help me diagnose. Whenever I compile code and I am listening to music I get this loud white noise burst that superimposes on the music and lasts a couple of seconds or so. Always happens when I compile the code and doesn't matter if I've got headphones on via BT or playing music through HDMI.

I'm not entirely sure but I don't actually think this is related to CPU usage as the compilation events that trigger the issue don't use up much CPU. On the other hand I've stressed the CPU in unrelated tasks and did not get any white noise. At this point I suspect of some sort of weird interaction whereby something in the coding/tooling chain I'm using (typescript, webpack and other JS tooling nightmare-inducing type crap) somehow is interacting with pulseaudio  and pushing data that comes out as white noise.

Anyone heard of anything like this? What would you recommend I do next to try and fix this? 

Running 20.10 with the unsupported kernel version 5.10.13-051013-generic because my machine is too recent and some components wouldn't work otherwise.

---

