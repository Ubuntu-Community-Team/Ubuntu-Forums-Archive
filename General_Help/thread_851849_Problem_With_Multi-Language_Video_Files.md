---
title: "Problem With Multi-Language Video Files"
date: 2008-07-07
forum: General Help
---

### Post by jlacroix on 2008-07-07
I noticed a weird problem today. I tried to watch some of the anime I downloaded (some *.mkv files) that have English and Japanese audio channels. While playing, if I switch the audio to English, the sound completely stops and then the video freezes. I tried the Dragon Player and also Totem which uses the Xine plugin. These same video files worked fine in Ubuntu 7.10. I tried playing them from the terminal to grab some output but there was nothing there that stood out as a cause.

Have any of you had this problem? Any help is appreciated. Thank you!

Edit: I also tried getting terminal output from Xine-ui, but there was no terminal output at all, good or bad.

---

### Post by kuja on 2008-07-07
I've found that VLC has the best support for Matroska containers (*.mkv).

---

### Post by Archmage on 2008-07-07
I use mplayer for watching thoese. With '#' I can change the audio. (Sometimes you need to go back to the start of the video so that it will be in sync.)

---

### Post by jlacroix on 2008-07-07
VLC seems to work fine with these files, thanks!

However, this is just a temporary fix, I'd still like to know why it's not working in the other players if you guys know why.

---

### Post by kuja on 2008-07-07
> **jlacroix said:**
> VLC seems to work fine with these files, thanks!

However, this is just a temporary fix, I'd still like to know why it's not working in the other players if you guys know why.

I would assume because the other players implementation of matroska support is buggy and/or incomplete.

---

### Post by jlacroix on 2008-07-07
> **kuja said:**
> I would assume because the other players implementation of matroska support is buggy and/or incomplete.

It worked in 7.10 though...

Have there been any regressions that you know of?

---

### Post by kuja on 2008-07-07
Nothing I know of ... I don't have any Matroska files on hand right now so I can't say much, but I do remember having issues playing them in other players in the past, but VLC handled them perfectly, so associating *.mkv files with vlc wouldn't be a bad idea. 

Off-topic: I'm wondering what's going on with VLC 0.9 development ... I've heard it will have switched from wxwidgets to Qt4, and I've also heard rumor of a VLC phonon backend .... hmmmmmmm

---

### Post by jlacroix on 2008-07-08
> **kuja said:**
> Nothing I know of ... I don't have any Matroska files on hand right now so I can't say much, but I do remember having issues playing them in other players in the past, but VLC handled them perfectly, so associating *.mkv files with vlc wouldn't be a bad idea. 

Off-topic: I'm wondering what's going on with VLC 0.9 development ... I've heard it will have switched from wxwidgets to Qt4, and I've also heard rumor of a VLC phonon backend .... hmmmmmmm

If they switch to QR4/Phonon that would be swell since I'm a KDE4 fanboy.

My only problem with VLC and KDE's Dragon Player is that the surround sound isn't all that good compared to Totem, I have surround sound speakers and Totem seems to be the only one that utilizes it well...

---

