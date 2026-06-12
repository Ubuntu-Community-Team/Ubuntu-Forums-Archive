---
title: "Need help in using prime offload with 2 nvidia cards"
date: 2022-02-27
forum: General Help
---

### Post by camsarria-k on 2022-02-27
Greetings

I have one Nvidia card wich is a titan Black 6gb with a hdmi port and a tesla m40 24 gb ram modded for gaming (has no hdmi port).

I need to use the tesla gpu for rendering and offload to the hdmi port of the nvidia titan.

Most manuals i find in the Internet are for prime  Intel nvidia combo or amd nvidia combo.

What i managed to do.

I install 470 driver séries and nvidia-prime because the titan is a kepler and if do a prime-run glxgears or vkcube i see the tesla working. But if i do a prime-run %command% the games render very slowly (doom eternal detects the 24 gb of the tesla but runs at 30fps).

Another thing i managed to do was switch the egpu (nvidia titan) with the dgpu (the tesla) and as egpu the tesla went to 60 fps as the main renderer using the titan hdmi port. I managed to somehow do this on a garuda os install with a mashup of several directions and sites wich was very heavy and unstable. I saved the xorg file installed manjaro and i cant replicate this. Wasted 2 days on this trying ubuntu kde reborn os manjaro etc and i cant replicate this. Does anyone know here how can i either 1 do a prime-run with decent performance on the dgpu or make the dgpu the default renderer? I dont mind installing kubuntu if it gets the job done. 
I rarelly ask for help but this one is getting me on the verge of insanity.

Thanks in advance
Carlos

---

