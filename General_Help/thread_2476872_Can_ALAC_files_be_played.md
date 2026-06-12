---
title: "Can ALAC files be played?"
date: 2022-07-10
forum: General Help
---

### Post by egshen on 2022-07-10
Hi all
I'm new to Ubuntu and have been a Mac user for 20 years.
All my music is in ALAC and I was wondering if these files can be read. Or if I'm going to have to convert everything in FLAC?
I  did some research on the subject but I don't totally understand the  answers. I know ALAC is an Apple format but it's my understanding that  it's been open source for some time, I assumed I could read them on  Ubuntu (maybe I assumed wrong...)

---

### Post by ActionParsnip on 2022-07-10
[https://packages.ubuntu.com/focal/alac-decoder](https://packages.ubuntu.com/focal/alac-decoder)

---

### Post by ActionParsnip on 2022-07-10
Could try VLC as well

---

### Post by Holger_Gehrke on 2022-07-10
In this [thread from 2010]("https://ubuntuforums.org/showthread.php?t=1500430") about converting ALAC Shantiq mentions vlc, QMMP, deadbeef, aqualung, xine, and audacious as being capable of playing ALAC. From my own experience I can add Clementine, rhythmbox, mpv and parole to the list of players. For conversion ffmpeg did the job back then and should still do it. For players using the gstreamer framework you might have to add one of the 'gstreamer1.0-plugins-{base,good,bad,ugly}' packages. So I'd say ALAC playback is a solved problem.

Holger

---

### Post by egshen on 2022-07-10
Thanks. I can actually read them from a usb stick but couldn't from my external HD (maybe because it's in HFS)

---

### Post by egshen on 2022-07-14
After installing all the gstreamer1.0-plugins and ffmpeg, Clementine is playing some ALAC files but not all of them. It's still saying there's a missing gstreamer plugin. Rhythmbox has the same issue and will only play some files (the same as Clementine).
Not too sure what to do at this stage apart from using VLC but that's not my favourite music player.

---

### Post by egshen on 2022-07-24
Please ignore my two previous messages that were just totally  inaccurate. Some AAC files got mixed up with ALAC files. I was going  too fast and since they have the same m4a extension, I thought some ALAC files could be played but that wasn't  correct.

I've spent the week doing more research and installed  all the gstreamer plugins (good, bad, ugly, base, libav) that were  recommended + alac decoder, ffmpeg, but I'm still stuck with the same  issue. Rhythmbox and Clementine won't play ALAC files and say gstreamer  plugins are missing. Soundconverter won't even let me convert the ALAC  files to FLAC (file not supported). Is there any way to know what plugin  is missing?

---

### Post by SeijiSensei on 2022-07-24
You could convert them to FLAC with ffmpeg. It's the "Swiss-Army-Knife" of audio/video manipulation.

[https://askubuntu.com/questions/123405/how-to-convert-alac-to-flac](https://askubuntu.com/questions/123405/how-to-convert-alac-to-flac)

---

