---
title: "Why Do I Have Two Sound Profiles; How Do I Remove One?"
date: 2020-02-24
forum: General Help
---

### Post by nakedgirl2 on 2020-02-24
On my computer and and on my friend's computer, we both have two sound profile.
Mine says:
HDMI / DisplayPort2
HDMI / DisplayPort

On my friend's computer, she has 
HDMI / DisplayPort 3
HDMI / DisplayPort

It keeps defaulting to the first one (HDMI / DisplayPort), which there is no sound. Her computer doesn't even have a DisplayPort; only HDMI.
She has to keep switching and it'll switch back if her computer has gone idle.
If she is watching a movie and pauses it and later, she has to switch it back again. I don't understand how that is possible or why that is.

How do we delete or at least select the default profile?

Thank you.

---

### Post by gdesilva on 2020-02-25
Go to Sound Settings (on my Ubuntu Studio it appears as the speaker icon on the panel - it may be different on your system. If you cannot find the icon, run command 'pavucontrol' on a terminal which should open up the sound settings window) and go to configuration tab. This tab enables you to turn on or off sound profiles.

---

### Post by nakedgirl2 on 2020-02-27
I turned the bottom one off, but it still shows on my 'Output' list.

---

### Post by gdesilva on 2020-02-28
You may have to reload pulseaudio as mentioned in the following link.

[https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

---

