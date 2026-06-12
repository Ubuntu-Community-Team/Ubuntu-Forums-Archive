---
title: "Sound Problems in Edgy Eft - Gaming"
date: 2006-10-11
forum: General Help
---

### Post by XVampireX on 2006-10-11
```
Hi, I'm having pretty serious problems with Edgy Eft Sound.

First of all, whenever I run into a website with alot of flash (with sound), it terribly slows down my computer/browser.

Next, I tried some SDL/OpenGL games, for example, an emulator called Mednafen, whatever game I try to play it slows down terribly (Well, not exactly slows down, but the sound stutters and along with it the game slows down, and it doesn't happen always, during gameplay, and sometimes it's okey and sometimes it's not), even with aoss. I tried ePSXe and the same thing happens with it, even during the movies.

It happens only in Edgy Eft.

What can I do?
```

Ok, I don't know how I fixed it, I restarted the PC after the newest edgy upgrade.

---

### Post by Gannin on 2006-10-11
What sound card are you using?

---

### Post by Robvdl on 2006-11-02
My friend is experiencing the same thing, she has an onboard NForce 2 sound card and I initially noticed slight stuttering on some open source 3D games, Chromium, Nexuiz, etc. Didn't think too much of it as it wasn't all that bad in those games, but the thing is that this didn't happen on my computer which has an Audigy 4 instead of an onboard card.

Then when I put Doom 3 on, it was terrible on the onboard card, stuttering.. sounded like a robot, and it's not because she has a slow graphics card, it's a 7600 GS AGP. The sound is perfect in Doom 3 on my Audigy 4, but terrible on her system with the NForce 2 sound card instead.

We are both running NVidia BETA 9xxx drivers on a GeForce 7, maybe the NVidia 9xxx drivers lock the PCI bus and the onboard card doesn't like it? I have heard of similar things in the past with Windows GeForce drivers locking the PCI bus ... not sure ... just a thought.

---

### Post by Gannin on 2006-11-02
Have you tried nVidia's nForce motherboard drivers?

---

### Post by Robvdl on 2006-11-09
There are no actual downloadable motherboard drivers from NVidia's website, other than the ones shipped with Ubuntu. The NVidia NForce drivers are open sourced and should already come built into the kernel shipped with Edgy.

This page confirms that:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

