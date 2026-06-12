---
title: "Error while initializing the sound driver"
date: 2005-06-22
forum: General Help
---

### Post by Darkscot on 2005-06-22
Can anyone shed some light on the following error message I get when running AmaroK?  If I click Ok the programme loads and works perfectly apart from playing any music, something of a disadvantage for this sort of application!  :? 

[I]
Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)
The sound server will continue, using the null output device.[/I]

---

### Post by bunced on 2005-06-22
It means another application is holding onto the /dev/dsp sound server. How to fix it...without seeing your PC, my telepathy is not good enough to fix it.

Regards
David

---

### Post by Darkscot on 2005-06-22
[QUOTE=bunced]It means another application is holding onto the /dev/dsp sound server. How to fix it...without seeing your PC, my telepathy is not good enough to fix it.

Regards
David[/QUOTE]

How come the other media players work (EG Totem) even when Amorok has been opened?

---

### Post by afonic on 2005-06-23
[QUOTE=Darkscot]How come the other media players work (EG Totem) even when Amorok has been opened?[/QUOTE]
 Hi there,

try installing amarok-xine (sudo apt-get install amarok-xine) as well as amarok-engines.

Then if you restart the problem in amaroK's settings you must have a seelction between the Arts and the xine engine. Select the xine engine and it should work just fine.

PS. Make sure you select Alsa and not ESD in the "Multimedia Systems Selector" (from System -> Perferences) if it doesn't work.
If even after that it doesn't work try: killall esd in the console.

Good luck!

---

### Post by Darkscot on 2005-06-23
[QUOTE=afonic]Hi there,

try installing amarok-xine (sudo apt-get install amarok-xine) as well as amarok-engines.

Then if you restart the problem in amaroK's settings you must have a seelction between the Arts and the xine engine. Select the xine engine and it should work just fine.

PS. Make sure you select Alsa and not ESD in the "Multimedia Systems Selector" (from System -> Perferences) if it doesn't work.
If even after that it doesn't work try: killall esd in the console.

Good luck![/QUOTE]

You Hero!!!  I did the 'sudo apt-get install amarok-xine' and it sorted the problem!  I also checked the settings afterwards and there only was xine engine so presumably that was the problem.  

Thanks a million!  \\:D/

---

### Post by afonic on 2005-06-23
[QUOTE=Darkscot]You Hero!!!  I did the 'sudo apt-get install amarok-xine' and it sorted the problem!  I also checked the settings afterwards and there only was xine engine so presumably that was the problem.  

Thanks a million!  \\:D/[/QUOTE]
 You're welcome.

Enjoy your amaroK!

---

### Post by cjoshuav on 2005-08-12
Fixed it for me too, thanks!

---

