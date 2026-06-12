---
title: "Choppy and bad video overall?"
date: 2006-11-01
forum: General Help
---

### Post by rozojc on 2006-11-01
Hi,

I recently installed Edgy, and I have been having trouble with my video... I used automatix2 for installing the w32codecs, but video playback is choppy, and in some cases it shows videos as if the files were corrupted, showing colors or other weird stuff for fractions of a second during playback. I know for sure that the video files I'm using are Ok, as I was using them with Zenwalk last week and they were fine...

What can I do?

---

### Post by tzulberti on 2006-11-01
Have you installed the "official" drivers of nvidia or ati (or whatever..)?

---

### Post by rozojc on 2006-11-01
I don't have an NVIDIA or ATI card... It's just an integrated Sis card. I actually had to manually edit the xorg file to make my laptop use the "sis" driver, as it was running through Vesa, which I assume is slower...But anyway I'm not trying to play opengl games or anything like that, I'm just trying to watch some movies...What's strange is that with Dapper and Breezy it was working great...

---

### Post by rozojc on 2006-11-01
Sorry to pop this up again, but still I haven't been able to solve the problem... Ideas please?

---

### Post by aknapp on 2006-11-02
I am having the exact same problem. I can't get the official NVIDIA drivers installed, so I am using 'nv' instead of 'nvidia'.

---

### Post by Jawbreaker4Fs on 2006-11-04
Same problem here, but I'm having the problem with an ATI card. Worked fine in Dapper?

---

### Post by tedrogers on 2006-11-11
I'm getting similar problems playing AVI/DIVX etc on full-screen...but its not so much a problem when windowed.

I only use VLC and can't get the regular Totem player to work - don't know if this is a codec thing (probably), but when you have VLC why use anything else. Furthermore, I don't really think it will solve the problem...cos if VLC can't play it then nothing can!

DVD's, however, run brilliantly from my DVDROM using VLC, and I'm running on a fairly slow machine (IBM T22, 800Mhz, 256MB RAM). So I was wondering if perhaps it was a DMA thing? So I checked using....

```
sudo hdparm /dev/hda
```

....and it was already on.

So if it's not that...then what could it be?

Any help appreciated. Thanks all.

---

### Post by SyberKowboy on 2007-07-11
Same here when in full screen. Running brand new laptop with Intel GMA950 chipset. It's super annoying because before Feisty I could play full screen with VLC no prob. I think I have all the right drivers too. Any ideas?

---

