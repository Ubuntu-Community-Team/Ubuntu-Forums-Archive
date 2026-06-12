---
title: "Alsa and Esd and OSS issues!"
date: 2005-07-19
forum: General Help
---

### Post by JoeUbuntu on 2005-07-19
Hi everyone, another long-winded post by myself coming right up!

Here's the situation. After installing Ubuntu (5.04), it detected and installed my soundcard (Terratec EWX 24/96) and everything fine, and sounds in gnome worked just perfectly (under multimedia selection it was set to esound).

After finally fixing up many things the way I wanted (shortcuts, interface, ati drivers etc.) I realised there was no sound in neverball (a little open source game that I like, in case nobody has heard of it). Same with all games. XMMS worked fine, and selecting ALSA in the multimedia selection dialogue and testing would result in an error.

I followed the guide ([www.ubuntuguide.org](www.ubuntuguide.org), or one of it's mirrors) in how to get sound in ubuntu working under alsa, and lo and behold, once the steps were completed ALSA and it's subsystems (alsamixer + gui etc) worked perfectly!

Only problem is, after rebooting X and running the multimedia config (gstreamer-properties I think) esound didn't work anymore! So I sacrificed sound in gnome for sound in games, which is hardly a satisfying solution. Typing esd in the terminal brings up an error informing me that my hardware is insufficient or something, fatal error etc.. P.s. the login screen sound (the drum taps) works fine!

Sorry for being long-winded but I'm on a windows pc at the moment so you'll have to bear with me, and apologies for the (possibly) simple question - I'm still just starting out with ubuntu and only have limited experience with linux previously.

---

### Post by codejunkie on 2005-07-19
[QUOTE=JoeUbuntu]Hi everyone, another long-winded post by myself coming right up!

Here's the situation. After installing Ubuntu (5.04), it detected and installed my soundcard (Terratec EWX 24/96) and everything fine, and sounds in gnome worked just perfectly (under multimedia selection it was set to esound).

After finally fixing up many things the way I wanted (shortcuts, interface, ati drivers etc.) I realised there was no sound in neverball (a little open source game that I like, in case nobody has heard of it). Same with all games. XMMS worked fine, and selecting ALSA in the multimedia selection dialogue and testing would result in an error.

I followed the guide ([www.ubuntuguide.org](www.ubuntuguide.org), or one of it's mirrors) in how to get sound in ubuntu working under alsa, and lo and behold, once the steps were completed ALSA and it's subsystems (alsamixer + gui etc) worked perfectly!

Only problem is, after rebooting X and running the multimedia config (gstreamer-properties I think) esound didn't work anymore! So I sacrificed sound in gnome for sound in games, which is hardly a satisfying solution. Typing esd in the terminal brings up an error informing me that my hardware is insufficient or something, fatal error etc.. P.s. the login screen sound (the drum taps) works fine!

Sorry for being long-winded but I'm on a windows pc at the moment so you'll have to bear with me, and apologies for the (possibly) simple question - I'm still just starting out with ubuntu and only have limited experience with linux previously.[/QUOTE]

you should be fine if you followed the guide at [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) if you wan't sound for events in gnome you should skip the part about ```
General Tab -> Sounds for events (Un-Checked)
``` and have sound events in gnome and apps.

---

### Post by JoeUbuntu on 2005-07-19
Hi Codejunkie,

Thanks for the quick reply, however "sounds for events" is checked and so is "enable sound server startup".

---

### Post by NeoChaosX on 2005-07-19
Did you check the Multimedia Systems Selector in Preferences and make sure ALSA is the default sink?

---

### Post by damonw5 on 2005-07-19
[QUOTE=JoeUbuntu]Hi Codejunkie,

Thanks for the quick reply, however "sounds for events" is checked and so is "enable sound server startup".[/QUOTE]
 Try installing "polypaudio" in Synaptic (or apt-get it). It's a "near-drop-in replacement for esound". Many find that it works better and solves some problems with esd. There are also plugins for it... you'd need to ask someone else if these are necessary as I don't know for sure.

---

### Post by JoeUbuntu on 2005-07-20
[QUOTE=damonw5]Try installing "polypaudio" in Synaptic (or apt-get it). It's a "near-drop-in replacement for esound". Many find that it works better and solves some problems with esd. There are also plugins for it... you'd need to ask someone else if these are necessary as I don't know for sure.[/QUOTE]

Hi damonw5, thanks for the help, however when I install polypaudio (with it's plugins) it breaks alsa again, in the same way esound did  :?

Possibly of note (for those that may have any ideas) is that the gnome sounds (and broken alsa) ONLY occurs when I install the polypaudio-alsa plugin. If that one is not selected, nothing changes.

---

### Post by JoeUbuntu on 2005-07-23
Hmm this is getting more frustrating. Seems I can only have EITHER game/movie/mp3 sound, or gnome sound. Why doesn't gnome use alsa for it's sounds? And why does the login screen play sounds fine?

---

### Post by arrowhead on 2005-07-23
Sorry JoeUbuntu  but I can't help with your question, I can only add that I too find this "workround"  a bit frustarting. IMHO it's the only thing that lets down Ubuntu, If this is fixed in the next release I would have no hesitation in handing Ubuntu discs to my friends.
Does anyone know if this will be fixed in the next release?

---

