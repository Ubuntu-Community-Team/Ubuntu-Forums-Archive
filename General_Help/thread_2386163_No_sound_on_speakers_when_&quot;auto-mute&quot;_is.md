---
title: "No sound on speakers when &quot;auto-mute&quot; is on. Pavucontrol shows Speakers (unavailable)"
date: 2018-03-01
forum: General Help
---

### Post by Viybel on 2018-03-01
No sound comes out of my laptop speakers when my headphones jack is plugged in and the "auto-mute" option is enabled in Alsamixer.

Disabling "auto-mute" in Alsamixer makes it possible to hear from speakers but deactivates auto-switch.

On Pavucontrol, tab "Output devices", the "Speakers" entry always shows "Speakers (unavailable)" and the Headphones always shows "Headphones (plugged in)", even when they are not plugged in.

Also, my laptop volume control buttons don't work anymore (nothing happens when I push them).

This regression seems to have appeared since I upgraded to Kubuntu 17.10 a few weeks ago (or maybe at a later update). It's been working all right for years.

I've spent a few hours already searching for solutions, but I couldn't find anything to help me.

Isn't there somewhere an explanation of the mechanisms and configs for how Pulseaudio/Alsa (I still don't know which) auto switches from headset to speakers on plugging/unplugging the headset? I'm a web developer and I'm puzzled by the complexity of  Pulseaudio/Alsa, which few people in the world seem to understand. Every  solutions that's suggested in forums look like magical incantations.

I tried the steps recommended there: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
(deleting config/removing/purging, etc.), including rebooting my machine.

Here is the ALSA Information Script output : [http://www.alsa-project.org/db/?f=4bb1e0d0e70a46e2163edeeb9356a18d31a9be2a](http://www.alsa-project.org/db/?f=4bb1e0d0e70a46e2163edeeb9356a18d31a9be2a)

Could someone help me?

Vianney

---

