---
title: "Skype Configuration"
date: 2006-12-02
forum: General Help
---

### Post by tocleora on 2006-12-02
I'm having problems getting skype working in Dapper.  I can hear myself speaking through the microphone but the other party cannot hear me.  Here's information:

1. I've tried both OSS and Alsa in Skype with same results.
2. In "Volume Control", Under "Capture" I have two options, "Capture" and "Capture 1". Both are enabled and volumes up.  
3. In "Volume Control", Under "Options" I have "Mic/Line Jack Mode" set to "Mic 80pc Bias".  "Input Source" is set to "Mic/Line".
4. If I run "Sound Recorder" and I record, I can hear myself in playback successfully.
5. Under Sound Preferences I've tried both "ESD" enabled and disabled.

I don't know what type of sound card I have, let me know where I need to find that if it's needed.

---

### Post by zgornel on 2006-12-02
You can turn Capture off, it will only direct the Mic input to the output, that's why you can hear yourself. Turn on Mic +20db boost (if you have it) and also the Mic Level Slider (main pannel). Worked for me out of the box. Play with your settings and try them out with the Skype Echo/Sound Test Service.

---

### Post by tocleora on 2006-12-02
No, capture was turned up almost all the way, I even yelled into it and no luck.  Echo123 is what I was testing with, then I got my daughter on there and tried every possible setting I could think of with no luck.

---

### Post by tocleora on 2006-12-02
SOLVED...

I uninstalled Skype and Reinstalled it.  I did download the deb from their web site and I don't know if it installed from the repo or from the deb I downloaded but whichever it did worked!

---

