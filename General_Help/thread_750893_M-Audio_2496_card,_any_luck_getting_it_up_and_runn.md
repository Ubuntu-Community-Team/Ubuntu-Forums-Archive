---
title: "M-Audio 2496 card, any luck getting it up and running?"
date: 2008-04-10
forum: General Help
---

### Post by SlappyPappy on 2008-04-10
I see some old posts about the M-Audio 2496 but not much in the way of success.

I was wondering if anyone has it running in Gutsy or better since it will be out soon, Heron?

I'm drooling at the thought of having this card and putting all my CDs on my new Linux box.

Thanks for any help you can provide and I'm hoping it's good news your posting here!    :)

---

### Post by Basotang on 2008-05-05
Hi,

With Gutsy, my Maudio 2496 is recognised out of the box, I had nothing to do (the onboard audio is disabled in the bios though).

With Hardy, I had to edit /etc/pulse/default.pa, as explained here [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)
It works-ish, but I get some annoying messages, like:
pulseaudio[6581]: alsa-util.c: Cannot find fallback mixer control "PCM".

Seb.

---

