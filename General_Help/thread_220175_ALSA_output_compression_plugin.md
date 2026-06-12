---
title: "ALSA output compression plugin?"
date: 2006-07-21
forum: General Help
---

### Post by ktulu1115 on 2006-07-21
I was wondering if there was any sort of plugin or other piece of software that interfaces with ALSA to provide compression - sound driver level so it'd application independent.  A quick Google search didn't provide much help to me - can anyone answer this?

---

### Post by christhemonkey on 2006-07-21
I know how i would do it, but it might not suite your setup.

Id rig the sonud through the JACK sound server, and then put all the outputs into jackrack, and put a ladspa (now called lash btw) plugin in.
Then connect the outputs into the audio out.

But i think it may be over kill for what you want.

Last time i checked XMMS had a compression plugin, but that is independently software based, which you said you didnt want.

---

