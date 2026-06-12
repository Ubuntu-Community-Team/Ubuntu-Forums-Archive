---
title: "Jerky Video"
date: 2007-02-21
forum: General Help
---

### Post by Zadok001 on 2007-02-21
So here's a weird one, at least by my standards.  I have a fairly nice graphics card, a Geforce 7800 GTX, factory overclocked.  I don't actually game all that much, but when I pull up even a simple game like Barrage or Emilia Pinball, I get strangely jerky graphics.  The in-game FPS meters show me as getting upwards of 400 FPS, which should be about right, given the hardware involved and the simplicity of the software, but every two or three seconds there will be a very brief pause in the rendering.  It's annoying as hell.

Oddly, this does *NOT* seem to occur in Beryl (which, yes, I've turned off - Issue remains), but it's rather difficult to tell.

I'm comparatively new to Linux, so please be gentle...

---

### Post by invalid on 2007-02-21
Have you enabled DMA on your hard drive? This helps in applications such as video players and the like.

---

### Post by Zadok001 on 2007-02-21
Well, I have no idea, but I doubt that would help.  Video, as in movie, is fine.  Only 3d games seem to have this issue.  Interestingly, sound is also jerky in games, but fine in movies.

---

### Post by Zadok001 on 2007-02-21
Well, I have no idea, but I doubt that would help.  Video, as in movie, is fine.  Only 3d games seem to have this issue.  Interestingly, sound is also jerky in games, but fine in movies.

---

### Post by crispy_420 on 2007-02-21
I think Ubuntu has DMA on by default now (?), even since 5.04. I may be wrong, so chime in if that is the case.

My guess would be video card not set up correctly. I don't have an NVidia based card but someone else may be able to help. Post your xorg, or atleast the part about your video card.

I see you also have sound issues, could you also post some basic system specs? What CPU do you have? Onboard audio? RAM? 

Also what resolution are you running games at?

Maybe you are pushing your CPU to hard?

Just a guess...

---

### Post by Zadok001 on 2007-02-21
3.6 GHz Pentium 4, 1 GB RAM.  I've been able to absolutely CRUSH similarly complex graphics in other OS's, and with framerates over 400, I'm fairly certain this isn't an insufficient hardware problem.  I *do* have onboard audio, so perhaps an underlying audio driver issue could be responsible.  The mobo is an Intel D925XCV.

I've been running at resolutions from 320x240 to 1024x768.  Issue is not only present at all resolutions, but consistent - Jerkiness occurs at the same regular intervals.

When you say "post your Xorg", I assume you mean this section of xorg.conf:

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Is that what you wanted?  :-)

---

### Post by Zadok001 on 2007-02-21
Just in case that's not weird enough for ya', get this - Planet Penguin Racer works flawlessly.  It is the ONLY 3D game I've located that works properly.  No stuttering, frame rates exceeding 100 constantly.

Confirmed - It's a sound issue.  Disabling sound solves the problem in other games.  So, um, how can I *FIX* it?

---

### Post by Zadok001 on 2007-02-22
Halp?

Here's where I am with this issue.  I'm fairly certain it's audio.  Programs that allow me to disable sound altogether run fine with sound disabled, programs that only give my volume controls are still broken with volume minimized.

If this were happening in Windows, I wouldn't hesitate to call it a driver issue.  Unfortunately, I have no idea how to find or install Ubuntu-compatible drivers for my on-board audio.  The D925XCV on Intel's site has a set of driver downloads, including "Linux" (they have drivers for SUSE and Redhat specifically).  But the instructions to install them don't work - They have me unzip the archive, then try to run "Configure" on the unzipped directories.  That doesn't work at all -  It claims it can't find the kernel.

Halp?

---

