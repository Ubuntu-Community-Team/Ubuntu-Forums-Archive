---
title: "No Audio From Totem or VLC"
date: 2005-04-19
forum: General Help
---

### Post by ZakZak on 2005-04-19
I get no audio from Totem or VLC.  Rhythmbox and Sound Recorder work fine.  Nothing helpful in the console output for Totem, but I did see this when I ran VLC:

[00000289] oss audio output error: cannot open audio device (/dev/dsp)

I tried switching the default sink in Multimedia Systems Selector to OSS instead of ESD but it didn't help.  I also rebooted after making that change and it didn't help.

I don't know much about how sound works in Linux, so I'm not sure what else to try...

-Zak

---

### Post by Vache on 2005-04-20
[QUOTE=ZakZak]I get no audio from Totem or VLC.  Rhythmbox and Sound Recorder work fine.  Nothing helpful in the console output for Totem, but I did see this when I ran VLC:

[00000289] oss audio output error: cannot open audio device (/dev/dsp)

I tried switching the default sink in Multimedia Systems Selector to OSS instead of ESD but it didn't help.  I also rebooted after making that change and it didn't help.

I don't know much about how sound works in Linux, so I'm not sure what else to try...

-Zak[/QUOTE]
 Did you follow the Sound How-To? Check out my sig for the link.

---

### Post by mandy2tom on 2005-04-20
[QUOTE=ZakZak]I get no audio from Totem or VLC.  Rhythmbox and Sound Recorder work fine.  Nothing helpful in the console output for Totem, but I did see this when I ran VLC:

[00000289] oss audio output error: cannot open audio device (/dev/dsp)

I tried switching the default sink in Multimedia Systems Selector to OSS instead of ESD but it didn't help.  I also rebooted after making that change and it didn't help.

I don't know much about how sound works in Linux, so I'm not sure what else to try...

-Zak[/QUOTE]
 I had same issue with preview and rc release but it seems to be fix in fixed in Release i386 
to make sound work I would run system monitor and kill ESD

---

