---
title: "No monitor output after several days of computer being on"
date: 2020-06-17
forum: General Help
---

### Post by anon5138 on 2020-06-17
Hello everyone,

So my issue is that after a few days of my computer being on, I'm no longer able to get any video output to my monitor from the graphics card.

The computer is my media server so it's meant to be on all the time. But also means I don't need to access it directly very often. However, even when I plug in a monitor every day and use it, I still have the same problem.

Specs:
Epyc 7351p 16c/32t
ASRock EPYCD8-2T
32gb DDR4 2400mhz registered ECC
Radeon RX580 gpu
Ubuntu 20.04 LTS with livepatch enabled
Latest BIOS version
Latest Mesa drivers (20.2.0-devel)

I've tried different monitors that work fine with my desktop. I've tried HDMI and Display port connections. Interacting with the mouse and keyboard initially activates the monitor but nothing is displayed and then it goes into power saving mode. 

Really my only option so far is to restart the computer, which of course I want to do as little as possible since it's a server.

I have no idea how to go about figuring out the issue so if anyone has any suggestions that would be much appreciated. Let me know if any other info would be helpful. Thanks!

---

### Post by dino99 on 2020-06-17
i suppose you need to set powersaving off via system Settings

---

### Post by anon5138 on 2020-06-17
Thanks for the reply.

Well under Settings > Power > Power Saving > Blank Screen, I just set it to 'Never' so I'll see if that helps at all. The computer is set to never suspend and I can still watch stuff from it without being able to interface at least.

---

### Post by anon5138 on 2020-06-18
Well sadly that didn't work and it still had no output. Any other ideas? The card is still active, I do hardware transcoding with it even when I can't get an output to a monitor.

---

