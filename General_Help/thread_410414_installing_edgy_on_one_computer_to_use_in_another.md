---
title: "installing edgy on one computer to use in another"
date: 2007-04-15
forum: General Help
---

### Post by FearMeansControl on 2007-04-15
hi,
i've come into posession of an old dell latitude ls laptop through a friend who destroyed the windows installation on it.  for those of you not familiar with this cool little piece of gadgetry, its tiny, and has no internal cd drive (came as a propietary external unit, i don't have this piece).  I had the idea to install ubuntu on the hard drive on a vaio laptop i have around (pcg-grt170).  It installs fine, and when i replace the drive in the dell laptop, it begins to boot, but i get a blue screen after the ubuntu loading bar finishes about the Xorg video not being setup correctly.  i think the problem here is that the sony has an nvidia card with dedicated memory, whereas the sony is 2mb shared.  I put the drive back in the sony, and am currently looking for some sort of video setup screen where i can get to change this.

here's another part.. if at that blue screen i click ok to read the video server output to make changes,  i can hit Esc., and get a screen about setting it up later, if you hit enter it takes you to a blinking underscore. after about 20 mins, i hit a key, and it allowed me to type. so does anyone know what kind of command prompt this is? sorry for being a n00b, but every time i go with linux, i end up trying a different distro. (this is my second crack at ubuntu, i tried out edgy when it was first released)

so does anyone know what i can do to fix this Xorg problem?

thanks in advance,
skye

---

### Post by spankymasterc on 2007-04-15
to fix the xorg problem boot into recovery mode and type 

> sudo dpkg-reconfigure xserver-xorg and follow on screen /...

---

### Post by FearMeansControl on 2007-04-15
thanks.. just one thing. how do i boot into recovery mode only having one OS on the machine? (i'm used to xp/linux and getting the option)

---

