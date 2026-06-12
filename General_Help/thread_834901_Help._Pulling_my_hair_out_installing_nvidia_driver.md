---
title: "Help. Pulling my hair out installing nvidia drivers"
date: 2008-06-19
forum: General Help
---

### Post by netvampire on 2008-06-19
I am running Mythbuntu. Everything is configured, except for one minor thing that is frusterating. Hopefully the experts on this forum can help meo ut.

My problem is it loaded some generic video driver upon installation. My video playback lags, so i tried to install the nvidias driver.

I went to nvidias site and looked up my card 8300 geforce.

I tried pretty much every driver there, 177, 173.14, 173.08 beta

none of them will work. I have an Asus M3N-HD motherboard, with an onboard graphics card. It has a 750a nforce chipset.

I am not sure what to do. I am right now running in "Low-graphics Mode" and cannot figure a way out of it.

I got pretty close with the 177 and 173.14 driver versions. Upon installation, if i directly loaded '/etc/init.d/gdm start' then i could boot into ubuntu and have Lag Free video at a high resolution. But the moment I reboot i get stuck back into "Low-Graphics Mode" ...Why wont the driver installation stick in place.


PLEASE HELP ME FIGURE THIS OUT. THANKS!!


Please ASSIST :)

Thank you.

---

### Post by Lexicon101 on 2008-06-19
> **netvampire said:**
> none of them will work.
What does it say when you try? It looks like they install fine, but they just don't have any output?

---

### Post by netvampire on 2008-06-19
they all say they installed fine.

however when i reboot i get into Low-Graphics mode....and it says it could not find a display driver.

However, the 177 driver worked fine after installation if i just ran gdm start. but the moment i rebooted it went back into Low-Graphics Mode. 

Any advice?

---

### Post by Lexicon101 on 2008-06-19
Hmmm. well, does it give any warnings during installation?
And have you tried the forums at nvidia too? always best to get as much input as possible..

---

### Post by netvampire on 2008-06-19
the only warning i saw was that it could not find a compiled kernel module for me and that it would do it from scratch...


i shall check the nvidias forum as well..thanks for the tip.

---

### Post by MindFlayer on 2008-06-20
Did you try to install drivers through the "restricted drivers" application?

---

### Post by sdennie on 2008-06-20
If the drivers only work until you reboot, see this thread: [http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2)

---

### Post by netvampire on 2008-06-20
i took a brief look on the nvidia forums and found the solution.

for those wondering, what u have to do is go into the synaptic packet manager, do a search for nvidia, and remove pretty much everything related to nvidia. that includes any restricted drivers, or kernel modules.

then once that is done, ctrl + alt + f1 to boot into command mode. then run /etc/init.d/gdm stop as root. and then sh NVIDIA_install_file 

that shall get you going.

thanks

---

