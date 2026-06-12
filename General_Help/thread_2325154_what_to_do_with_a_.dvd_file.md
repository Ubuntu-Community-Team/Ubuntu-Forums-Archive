---
title: "what to do with a .dvd file?"
date: 2016-05-19
forum: General Help
---

### Post by opfeld on 2016-05-19
I finished making a slideshow movie for my son's school and export the project from openshot using the DVD profile.  The ouput file I am getting is a .dvd file type, 38.7MB which seems small, and it seems like nothing knows what to do with it.  Brasero couldn't open it, Devedo couldn't open it, Bombono couldn't open it, Mplayer couldn't play it, nothing.  However if I export the same project to the YoutubeHD profile, I get a 2GB .mp4 which looks and works great.  Problem is when I transcode the .mp4 to a dvd using bombono, the quality takes a big hit.  Does anyone know how to properly make a playable dvd from a .dvd file?  Or any other suggestions?

---

### Post by mc4man on 2016-05-19
May be good to note what release of Ubuntu you have.
openshot would export as a mpeg-ps file (mpeg2video) which then would need to be authored to DVD VIDEO & burned to disk if desired.
Any decent player should open the .dvd file, the extension is not really relevant.

Maybe install mediainfo-gui to ck. your .dvd file, should be about what is in scr.1
dvdstyler is an easy dvd authoring app to use, it has no issue here with an openshot dvd project file, scr. 2. Because the project file was already the proper file type for dvd video it just used ffmpeg to copy the audio & video & it authored to the proper format for DVD VIDEO, scr.3

---

### Post by opfeld on 2016-05-20
Hmmm I will check out mediainfo when I get home, work nights.  However looking at yours I think openshot is incorrectly exporting to the DVD profile cause my project is 18 minutes long and about half the MB of yours, which is 4 minutes long.  I was thinking of trying to export it to an XML and open it with kdenlive and see if that works.  Thanks for the input

---

