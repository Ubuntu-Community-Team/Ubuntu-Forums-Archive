---
title: "Problem with Audio tab in winecfg"
date: 2007-06-10
forum: General Help
---

### Post by Aikon- on 2007-06-10
I'm currently trying to get the sound working for StarCraft on Wine. The sound works fine for Ventrilo or WoW, but only if nothing else has the sound card active. However for StarCraft, I'm not getting any sound.

I went to **winecfg** to see if there were any settings I could fiddle with that might get it working, but whenever I try to click on the audio tab, the Wine window becomes unresponsive and I get the following error in the terminal:

```
sarmitage@OPHELIA:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** free(): invalid pointer: 0x7c06cce8 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

```

Any help would be greatly appreciated.

Thanks,
-Aikon

---

### Post by christhemonkey on 2007-06-10
That sounds like an error to do with one of the midi settings (ALSA to be specific).

If you type this then it should get rid of the first line:
```
sudo modprobe snd-seq 
```

But the invalid pointer and assertion failing part shouldnt happen.
See if it still does after you have run that line of code?

---

### Post by Aikon- on 2007-06-10
I've been browsing around some archives while waiting for a response and I had just stumbled on the sequencer for the /dev/snd/seq bit. I ran modprobe to load the sequencer and sure enough, the first line goes away. However the other two remain:

```
sarmitage@OPHELIA:~$ winecfg
*** glibc detected *** free(): invalid pointer: 0x7c06cce8 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

```

---

### Post by Aikon- on 2007-06-11
Any ideas about the invalid pointer / assertion failure?

---

### Post by Aikon- on 2007-06-12
I fixed the 2nd two lines by the following:

```
sudo mv /usr/lib/wine/winearts.drv.so /usr/lib/wine/winearts.drv.so.old
```

Then when I ran winecfg and clicked the audio tab, I got an error about libjack being missing; this persisted until I installed all four of the following packages:

[LIST]
[*]libjack0.100.0-0
[*]libjack0.100.0-dev
[*]libjackasyn0
[*]libjackasyn-dev
[/LIST]

After installing those packages, I could click the Audio tab fine and get my sound working in Starcraft.

Thanks Chris for your initial help.

-Aikon

---

### Post by christhemonkey on 2007-06-12
No worries, gald you managed to sort out your invalid pointer issues.

Please consider filling a bug against wine as that (obviously) isnt meant to happen!

---

