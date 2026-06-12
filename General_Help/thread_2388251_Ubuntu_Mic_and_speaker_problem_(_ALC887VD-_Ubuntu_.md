---
title: "Ubuntu Mic and speaker problem ( ALC887VD- Ubuntu 10.04 )"
date: 2018-03-30
forum: General Help
---

### Post by sbahadirarslan1 on 2018-03-30
Hello,
I am trying to use my mic and speaker, but both is not working. 

In my motherboard, ALC887-VD audio codec is exist, and also I am using Ubuntu 10.04
With this board and and the ubuntu version, external mic and speaker is not working. 

When I upgrade the ubuntu to 16.04, both external mic and speaker is working. So I decide that, hardware is working well.
Also I tried another motherboard that contains ALC889 audio codec. With ubuntu 10.04 and the this hardware, external mic and speaker is working good.


I added options 
[B][COLOR=#CC0000]options snd-hda-intel model=generic 
[/COLOR][/B]to the /etc/modprobe.d/alsa-base.conf, but this is not solved my problem.

So How can I ubuntu 10.04 with the ALC887-VD codec properly ? 
Thanks and best regards.

---

### Post by Yellow Pasque on 2018-03-30
If it works in a newer release, the logical solution is to run a newer kernel, or at least newer sound modules. You can't do that because you're running such an outdated release that has reached End of Life.

---

### Post by sbahadirarslan1 on 2018-03-30
I can't use the newer release, One software in my system has dependency with some kernel modules.
So this is not options for me. Thanks anyway.

Any recommends ?

---

### Post by Yellow Pasque on 2018-03-30
> **sbahadirarslan1 said:**
> Any recommends ?

Run the program that requires old dependencies in a VM.

---

### Post by sbahadirarslan1 on 2018-03-30
Thanks but I want to work with ALC887-VD codec and Ubuntu 10.04. Is it possible ?

---

