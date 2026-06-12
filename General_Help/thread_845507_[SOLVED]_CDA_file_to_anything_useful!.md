---
title: "[SOLVED] CDA file to anything useful!?"
date: 2008-06-30
forum: General Help
---

### Post by argraff on 2008-06-30
I hope someone knows something about this! I've been searching all day.

A client sent me a cda file to turn into an mp3 and make available on her website. I can't seem to find any program or codec to turn the file into an mp3 or ogg, and I can't seem to burn it to CD to re-rip. I've got all of the medibuntu stuff installed, gstreamer, etc. I'm at a loss.

All of the posts I've found here and elsewhere were about how to get an audio CD to rip to mp3 - I don't have a CD to start with, only a file.

Help???

---

### Post by doug1212 on 2008-06-30
I think i would try changing the extension to .wav and try to open with an audio player and if it plays ok use "lame" to convert to .mp3 or "oggenc" to convert to .ogg.
good luck,
Doug.

---

### Post by coolaj86 on 2008-06-30
CDA files on original CDs are simply small breaks between songs. They contain no useful information (meaning convertible data)

On pirated CDs (not direct copies, but created using an intelligent audio burner or unripped from MP3s, etc) the CDA files can be renamed to .wav and then converted to MP3.

You can 
sudo apt-get audacity
(or Applications > Add/Remove... > Search: Audacity if you prefer)
and it should be fairly obvious how to convert the file. I don't have it installed ATM, but I believe there is a 'save as' or 'convert'. Rythmbox may also have a similar feature.

Of course, there's a good chance you'll just have to get your client to send you the music again in the correct format. A typical CDA/WAV can't be sent through e-mail because it's HUGE - 30mb+.

Some people on the forums might suggest shooting me for suggesting this... but you might ask your client to install iTunes, go into the burning options to change it to mp3, and rip the CD correctly.

---

### Post by argraff on 2008-07-08
Y'all are right - the cda is nothing (a couple of kbs). I've asked her to resend it in *any* other format! Thanks!

---

