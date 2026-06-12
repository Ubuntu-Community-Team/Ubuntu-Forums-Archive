---
title: "Audacity wont record after one track"
date: 2008-05-20
forum: General Help
---

### Post by Patrick-Ruff on 2008-05-20
hey all, in audacity after I record one track if I try to record a second track over that one by hitting the record button audacity says "Error while opening sound device. Please check the input device settings and the project sample rate."

any idea's on what would cause this?  I'm running hardy heron that I upgraded from beta.  hopefully that isn't relevant as I don't want to format :).

---

### Post by ibuclaw on 2008-05-20
Are you using PulseAudio or Jack as your sound server to record?

Try switching to Jack first, If you still fail, turn off Jack and then try settings your Sound Devices so that they are all pointing to te ALSA driver control for the soundcard you are recording off.

If all else fails, I tend to use **asoundconf-gtk** to set my main soundcard device in Linux.

Regards
Iain

---

