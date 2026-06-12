---
title: "Gstreamer plugin error- Clementine"
date: 2014-05-15
forum: General Help
---

### Post by cincibluer6 on 2014-05-15
I have no idea what's going on but Clementine repeatedly throws me errors regarding music playback. Steps I have taken include:
1) updated to the latest via the Clementine PPA.
2) checked that I had ubuntu-restricted-extras (latest is installed.)
3) Installed EVERY libgstreamer-plugin via synaptic.
4) Checked my locale and made sure US_en_UTF-8 was in there.
5) ran in terminal for error checking.

So basically, none of that has helped and the errors were Gstreamer 572 and GstreamerPipeline562 (IIRC.) Not sure where to turn from here. Doesn't seem to be any rhyme or reason to why it is acting up (though I'm guessing that maybe one of the plugins is incorrectly configured or something.)

Any ideas? Running Ubuntu Gnome 14.04 with all packages updated/upgraded.

---

### Post by cincibluer6 on 2014-05-16
Think I found the answer. Apparently it's the WMA files.

Anyway, huge thanks to Sylvain (along with the repo owner) for the answer.

[http://askubuntu.com/questions/456072/clementine-wont-play-wma-with-your-gstreamer-installation-is-missing-a-plugi](http://askubuntu.com/questions/456072/clementine-wont-play-wma-with-your-gstreamer-installation-is-missing-a-plugi)

Basically, it needs gstreamer0.10-ffmpeg but the ubuntu repos don't have it. Add the PPA, update, and install that and you're good to go.

---

