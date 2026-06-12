---
title: "Winff"
date: 2016-09-05
forum: General Help
---

### Post by Shobuz99 on 2016-09-05
> **ajgreeny said:**
> Just for the record, it looks as if that ppa has not been updated for almost 4 years, so is very unlikely to work now except in Precise 12.04.

This thread is close to what I'm looking for, for an answer. Let me know if I need to start a new thread.

My question is: Which would be the better option for me to run Winff to convert a file to a .mp4 that I want to get from a homemade DVD.
The DVD was burned directly from a vintage VHS tape, that are the "trims" from the movie "Casino".
My friend was in the film, and Martin Scorsese sent him a rough cut, including scenes he did that were cut...
My friend wants to use this for a demo to show someone in the film business.

I have two options:

[LIST=1]
[*]Swap out the **14.04 LTS** system *without* Winff installed and swap in my old **10.04 LTS** system that already has Winff installed and then do the conversion... OR
[*]Simply install Winff on my  drive, set it up and try doing the conversion with that.
[/LIST]

I'm concerned that because **10.04 LTS** is no longer supported or able to update any pkgs, 
if I run into a problem with the PPA issue posted here

However, I don't know what to anticipate during an install of Winff on my **14.04 LTS** system.

This is not a dual boot issue, since I'm literally swapping SATA drives out and in from my laptop...
I need to know what the best option would be and what the dependencies might be, too.
I've been asked by my film producer friend to do this quickly because he can't do it.

Thank you for your help.. I do appreciate it

Shobuz99 (Rick)

---

### Post by Shobuz99 on 2016-09-06
Bump

---

### Post by howefield on 2016-09-06
Post moved to its own thread and to the "*General Help*" forum.

---

### Post by Shobuz99 on 2016-09-06
> **howefield said:**
> Post moved to its own thread and to the "*General Help*" forum.
Thank you. :-)

---

### Post by mc4man on 2016-09-06
While winff may use some outdated syntax it still should work fine. It's still updated so you can use in whatever version of Ubuntu you got going.
In any event any (ffmpeg/libav) option can be edited prior to encoding if need be or any preset can be altered (in ~/.winff/presets.xml

---

### Post by FakeOutdoorsman on 2016-09-07
If it is a typical video DVD then handbrake is your easiest solution.

if it is just a data DVD with a normal video file then you can use ffmpeg directly. Since you mentioned a VHS I'll assume it's interlaced so you can use yadif to deinterlace.
```
ffmpeg -i input -vf "yadif,format=yuv420p" output.mp4
```

---

### Post by Shobuz99 on 2016-09-07
Thank you. I will!

Shobuz99

---

### Post by Shobuz99 on 2016-09-07
> **FakeOutdoorsman said:**
> If it is a typical video DVD then handbrake is your easiest solution.

if it is just a data DVD with a normal video file then you can use ffmpeg directly. Since you mentioned a VHS I'll assume it's interlaced so you can use yadif to deinterlace.
```
ffmpeg -i input -vf "yadif,format=yuv420p" output.mp4
```

Do I actually need to de-interlace it before I convert it to a MP4 file?? 

Thank you. I appreciate it.

Shobuz99

---

### Post by FakeOutdoorsman on 2016-09-07
> **Shobuz99 said:**
> Do I actually need to de-interlace it before I convert it to a MP4 file?? 

No, but consider doing so if the input is interlaced. Otherwise you may see combing artifacts in fast motion scenes.

---

### Post by Shobuz99 on 2016-09-07
> **FakeOutdoorsman said:**
> No, but consider doing so if the input is interlaced. Otherwise you may see combing artifacts in fast motion scenes.

Combing artifacts??? You lost me.

This VHS video was transferred/burned directly to DVD. I have no idea how to tell if it is interlaced.
It was done on a home computer with a Windows OS--maybe Vista or possibly Win7.....

Shobuz99

---

