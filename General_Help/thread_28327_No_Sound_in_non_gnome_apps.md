---
title: "No Sound in non gnome apps"
date: 2005-04-19
forum: General Help
---

### Post by Sonic-NKT on 2005-04-19
Hi,
sound is working in gnome.. i cant controle it with the main mixer but with the applications like rhythmbox, totem, Gaim.. etc
now i thought i install some other applications like dosbox, scummvm...
but in those it gives an error with the sound hardware. also in flashprograms which run in Firefox the sound doesnt work.
has gnome a special soundserver running which other applications cant use and so the sound device is allready in use?
btw, i use a SIS onboard soundcard..

EDIT:
ok killed the sound server and now it works. except dosbox.. :(

EDIT2:
ok works now..

one thing still missing... midi ;)

---

### Post by satoshi on 2005-04-20
[QUOTE=Sonic-NKT]Hi,
sound is working in gnome.. i cant controle it with the main mixer but with the applications like rhythmbox, totem, Gaim.. etc
now i thought i install some other applications like dosbox, scummvm...
but in those it gives an error with the sound hardware. also in flashprograms which run in Firefox the sound doesnt work.
has gnome a special soundserver running which other applications cant use and so the sound device is allready in use?
btw, i use a SIS onboard soundcard..

EDIT:
ok killed the sound server and now it works. except dosbox.. :(

EDIT2:
ok works now..

one thing still missing... midi ;)[/QUOTE]
 How did you fix it?  I'm having the same problem with DOSBox and I would love to be able to have sound when I play Jazz Jackrabbit...

---

### Post by jobezone on 2006-01-14
For having sound in dosbox, see what erro you get when you run dosbox in the terminal window. Probably for Jazz Jackrabbit you'll just have to configure it (inside dosbox) to use soundblaster for special effects, and adlib, or soundblaster (or midi) for music.

For software synthesis (software Midi) to work in the system: [https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo?highlight=%28midi%29](https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo?highlight=%28midi%29)

For midi sound in dosbox, see if my advise works. It's the last comment at the thread [http://ubuntuforums.org/showthread.php?t=63081&page=2](http://ubuntuforums.org/showthread.php?t=63081&page=2)

---

