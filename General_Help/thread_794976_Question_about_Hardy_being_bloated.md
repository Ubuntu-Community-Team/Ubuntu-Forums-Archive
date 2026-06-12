---
title: "Question about Hardy being bloated"
date: 2008-05-15
forum: General Help
---

### Post by M_Alex on 2008-05-15
I loved gutsy. Mainly due to the fact that i have ubuntu on my laptop, which is a rather simple piece of equiptment, which happened to be equipt by default with vista - guess how that works.

After I installed Hardy, things went worse, then a lot of updates came out, and it got better - but not as good as gutsy. As my laptop is mainly a workstation (well, typewriter with compiz on it actually might be more accurate) i would want it to work as efficiently as possible.

The question is:

Will Hardy reach the level of efficiency that gutsy had?

I'm not saying that i don't like hardy (actually even if everybody states here that hardy won't be as efficient as gutsy i'm still not sure if i'll go back, there are things that i'm expecting from it as an LTS - and i can wait for the first milestone). Negative hype or no, i do think that hardy works slower on certain occasions, such as the booting of the system (i'm sure of this). It had problems with shutting down, but they were fixed.

I have a special affinity for gutsy; it wasn't the first ubuntu distro that i used, but it is the distro which caught my heart and made me stick to it, at least on the laptop.

---

### Post by Jouke74 on 2008-05-15
I suggest staying at Hardy:

There is LTS support, meaning you can keep this one longer. Although I cannot see why you can't use Gutsy as long as you like as well. The power saving functions of the Kernel should be better on Hardy though.

Hardy has bugs, Gutsy did too. In time they will be fixed. 

For the slowness you mentioned:

1. Install the compizconfig - settingsmanager.
Disable the window fading and animations or reduce the time of fades. It speeds things up drastically.

2. Profile your boot sequence.
- When you see the Grub menu boot loader (might require Esc) edit your kernel line and add "profile" at the end just for this session!

- Don't save it, just press "B" to boot. 

- Now it will profile your whole boot and reorder the files to make it quicker. This boot will be very slow!

- After it's done, next time you will boot up your laptop again it will boot faster.

3. If you're not using it, uninstall the tracker software. 

4. Increase your memory use of the OpenOffice applications (assuming you're typing in those). It's somehwere under the settings.

---

