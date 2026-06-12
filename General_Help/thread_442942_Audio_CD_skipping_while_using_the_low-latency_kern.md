---
title: "Audio CD skipping while using the low-latency kernel in ubuntustudio"
date: 2007-05-14
forum: General Help
---

### Post by jsmanness on 2007-05-14
Hello,

I have ubuntustudio installed with both the generic and low-latency kernels.  I noticed that using the low-latency kernel made my audio CD skip in Amarok, VLC, and Sound Juicer.  I am assuming that it's the kernel because my CD doesn't skip using the generic kernel or in XP.  I was wondering if the skipping is due to not having a professional sound-card to handle the low-latency kernel.  I do have a powerful desktop (E6600 Duo-Core with 2 Gig Ram) so I can't think of what else it could be.

Thanks,

Jon

---

### Post by tgalati4 on 2007-05-14
The low-latency kernel guarantees 95% of the CPU cycles to go the current audio application that is marked to grab the kernel.  If you run Audacity to record a 2-hour concert directly to harddisk, you will find that the mouse/cursor is sluggish, and doing anything else is difficult because Audacity is guaranteed 95% CPU time.  This means that you get a 2-hour recording, reliably, every time.

I don't believe the music players are marked to grab the kernel.  They probably could be, but that is beyond my expertise.

The type of sound card really doesn't matter.  What does matter is using an application that is pegged for real-time kernel use.  It's a special application tool.  The media players are competing for the 5% CPU cycles, so of course it will skip.

You use the real-time kernel for recording or editing music in Audacity or any of the other music editors contained in Ubuntu Studio.

If you want to listen to music, then you will need to boot into a regular kernel.

---

### Post by jsmanness on 2007-05-20
Makes sense to me.  Thanks for the explanation.

---

### Post by eye208 on 2007-05-22
> **tgalati4 said:**
> If you want to listen to music, then you will need to boot into a regular kernel.
If this is true, then audio production on Linux will never fly. On Windows I can use Cubase at low latencies *and* listen to audio CDs using any media player without skipping.

Therefore I would like to know whether this problem has been confirmed by other users of the low-latency kernel.

---

### Post by tgalati4 on 2007-05-22
There are several audio playing applications and several audio architectures under Linux.  If you listen to music using Lsongs (under Freespire, for example), you are running a Python interpreter which eats 50 to 100% of the CPU just to play music.  If you use XMMS, then perhaps 3 to 5% of the CPU is used to decode the mp3 stream and send it to the sound card.

Windows has some decent audio editing programs available.  There are decent ones on the Mac platform as well.  

One would need to make a matrix of music players versus Linux sound architectures (alsa, oss, esd, etc) to really compare music-playing performance on a real-time kernel.

The low-latency kernel is for special application use, not general desktop use.  The mouse and desktop redraw can be sluggish under the real-time kernel as well--especially if you are recording music.  This is an annoyance, but less so than your music-recording program crashing because of a buffer underrun.

If you have a music-production toolkit that works for you under Windows then stick with it.  If you don't, then Ubuntu Studio or Dynebolic provide a free way to get into music production--warts and all.

---

### Post by eye208 on 2007-05-22
The original post mentioned quite a few music players including VLC which has never appeared badly optimized to me. The point is, if low-latency kernels are unusable for these basic tasks such as playing a CD even when no audio production software is hogging the system, then Linux will never have a chance of competing against Windows in that area.

On Windows, when load is too high in Cubase, the user interface will get sluggish too, but the application will not crash when a buffer underrun occurs. On the other hand, if Cubase is not putting a strain on the system, CDs will play just fine in any media player. The same thing should be possible with Linux too, low-latency kernel or not.

---

### Post by tgalati4 on 2007-05-24
As a rule of thumb, on older hardware(PII 300MHz to PIII 1GHz), use Dynebolic for music production.  For newer hardware, Ubuntu Studio should be fine.  It's possible that some of the music players have not been recompiled or optimized for low-latency. 

I do get mp3 skipping on Dynebolic on a PII, 300 MHz machine, but that's running Banshee with a music share from LSongs on a Freespire machine that is using a SAMBA share from a P1, 166 MHz Damn Small Linux machine.

When I open Audacity or any other major audio application then the mp3 stutters will occur.  I haven't determined where the bottleneck is:  CPU, network, disk I/O, nice priority, etc.

Low-latency is really designed for single-task computing.  When you multitask, you can expect that two real-time applications will take a hit.

---

