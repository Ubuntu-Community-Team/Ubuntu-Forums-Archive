---
title: "Laptop speaker cuts out after 3 mins, headphones still work fine"
date: 2015-09-17
forum: General Help
---

### Post by bob150 on 2015-09-17
Hi, I have been using ~buntus for a few months now, but I have had a problem on my new laptop

It is a lenovo x201 and after about 3 minutes from turning the computer on, the main speaker audio cuts out, however I still recieve audio from headphones with no problem

I have tried Xubuntu, Mint and Opensuse and I have the same problem on each of them

Does anyone know what I could do here, I'm completely stumped. The audio worked fine when windows was installed so it is a software issue by the look of it. If I restart the computer the audio form the main speakers comes back on, but only for about 3 minutes like before. Obviously this is not ideal

Thanks

---

### Post by tgalati4 on 2015-09-17
It's possible that the audio amplifier that drives the speakers has crapped out.  You will still get audio for headphones because that is driven directly by the sound chip, but the speakers go to a separate amplifier chip that gets hot and cuts out after 3 minutes.  I bet if you installed Windows back on this machine, you would find similar behavior.  I presume that machine is not dual-boot, so you could test that it works in Windows consistently, but not in Ubuntu.  

Lenovo's/Thinkpads have Intel sound hardware and the drivers generally work pretty well.

---

### Post by bob150 on 2015-09-18
> **tgalati4 said:**
> It's possible that the audio amplifier that drives the speakers has crapped out.  You will still get audio for headphones because that is driven directly by the sound chip, but the speakers go to a separate amplifier chip that gets hot and cuts out after 3 minutes.  I bet if you installed Windows back on this machine, you would find similar behavior.  I presume that machine is not dual-boot, so you could test that it works in Windows consistently, but not in Ubuntu.  

Lenovo's/Thinkpads have Intel sound hardware and the drivers generally work pretty well.

I see, so is there anyway that this could be fixed?

---

### Post by tgalati4 on 2015-09-18
Open the laptop and put your finger on the amplifier chip.  It's probably really, really hot.  Press down on it hard, to see if makes connection.  Sometimes the chips fail by delamination.  They get hot, warp, and lift off of the motherboard, causing a break in electrical connection.  There is no software, or magic configuration fix.

Where you playing this laptop in steaming mode for long periods of time?

---

