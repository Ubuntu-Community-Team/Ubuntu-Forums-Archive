---
title: "possible to forward sounds from one machine to another?"
date: 2008-02-25
forum: General Help
---

### Post by Wolfghar on 2008-02-25
I've got 3 boxes, one I just setup as a media box and it's connected to my speakers, another is my main box and it doesn't have speakers, is it possible to forward sounds from my main box to my media box to play through the speakers?

Both machines are running Ubuntu 7.10

Regards,
Wolfghar

---

### Post by sp0nge on 2008-02-25
You might want to consider using the Terminal Server Client to access the main box from the media box and you can play the remote sounds on the local machine. 

Alternitavely, you could consider something like logmein.com and enable yourself to access the main machine from any machine anywhere. 

I use both as well as window's remote desktop application when needed and my life has been much simpler for it. 

Hope this helps.

---

### Post by Wolfghar on 2008-02-25
I already use my main box to access remote desktop on my media box, but what I'd like is to be able to hear stuff on my main box (youtube, etc), so that is why I'd like to forward audio from my main box to my media box to hear audio from my main box as well as my media box (since the media box has the only set of speakers)..

Wolfghar

---

### Post by sp0nge on 2008-02-25
I don't think you'll be able to make the main box audible if there are no speakers.

---

### Post by sammydee on 2008-02-25
It is possible to do what you're asking with network transparent sound daemons like pulseaudio.

Pulseaudio in gutsy seems to break most of my alsa and oss sound, so I would recommend holding off until hardy, which includes pulseaudio by default.

Sam

---

