---
title: "no MIDI playback"
date: 2008-05-25
forum: General Help
---

### Post by jakupl on 2008-05-25
I as a music student need midi to work.
When I try to play midi files, regardless of playback engine, it looks at though it is working, but I never get any sound output.
Do you know a possible solution for this?

thanks in advance.

---

### Post by jakupl on 2008-05-25
bump

---

### Post by ibuclaw on 2008-05-25
My MIDI playback is fine as is.

Not sure why, or how to fix yours, but the packages I have installed (When I searched for "MIDI" in synaptic)
Are:
[LIST]
[*]alsa-utils
[*]freepats
[*]libsdl-mixer1.2
[*]libwildmidi0
[*]lilypond
[*]rosegarden
[/LIST]
Maybe that combination will work for you?

Regards
Iain

---

### Post by jakupl on 2008-05-25
thankyou very much. I can now playback .mid files in totem, but i still can't do what I really need it for.
It still behaves the same way in roseguarden and in NoteEdit

---

### Post by ibuclaw on 2008-05-25
Hi, sorry for the delay.

The only possible fix that comes to mind is one I did for Tuxguitar when MIDI wasn't playing for that app.

If you haven't got alsa-oss installed already, do so.
```
sudo apt-get install alsa-oss
```

Then edit the Menus so that the commands for Rosegarden and NoteEdit have **aoss** infront of them.
ie:
```
**aoss** foo-application
```

Regards
Iain

---

