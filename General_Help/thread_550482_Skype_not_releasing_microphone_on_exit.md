---
title: "Skype not releasing microphone on exit"
date: 2007-09-13
forum: General Help
---

### Post by krigare on 2007-09-13
Hi,

I've got Skype set up and making calls just fine, but it seems like it's not turning off (releasing?) the microphone after a call, or even after I close the program.

If I tap on the microphone I can clearly hear it through my speakers. Even typing echoes.

This sounds similar to what is described here:

[http://juljas.net/linux/skype/#sound](http://juljas.net/linux/skype/#sound)

except that Skype has no problems starting up again and other apps can use the speakers.

pgrep-ing for skype, esd or dsp all come up empty..

I'm running Xubuntu 7.04 on a Dell 600m; Skype version 1.3.0.53_API.

$ uname -a
Linux ghost 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

Any idea what I can do to kill whatever it is that's still connected to my mic?

Thanks!

---

### Post by startherepodcast on 2007-09-14
Hi,

Before you start skype do you still hear you mic through your speakers?

---

### Post by krigare on 2007-09-14
I don't hear the mic through the spakers before I start Skype the very first time, but then the mic stays "on" even after I close Skype...  Sometimes even a reboot doesn't even help.

---

