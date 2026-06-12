---
title: "Firefox permissions broken"
date: 2006-08-14
forum: General Help
---

### Post by Malta Soron on 2006-08-14
Hello everyone,

I was following [this guide](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix) and came at [this point](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Firefox.2C_Mozilla.2C_RealPlayer.2C_Skype_.26_Co):

> Firefox, Mozilla, RealPlayer, Skype & Co

To make its plugins (especially libflashplayer.so) use dmix through aoss:

    * Move the original firefox symlink 

```
# rm /usr/bin/firefox
# ln -s /usr/libexec/mozilla-launcher /usr/libexec/firefox
```

    * Create a new executable script: 

File: /usr/bin/firefox

```
#!/bin/sh

# This line needs to be maintained or Thunderbird (and
# certain other apps) will not launch links when they
# are clicked on
export MOZILLA_LAUNCHER=firefox

# not correct:
#aoss /usr/libexec/firefox $*
#
# correct:
aoss /usr/libexec/firefox "$@"
```


    * From my experience with Firefox 1.5.x (source, not bin), you don't need to do that stuff above, just edit last line of /usr/bin/firefox - insert aoss after exec 

```
# exec aoss /usr/libexec/mozilla-launcher "$@"
```

I didn't know what to do with the last line, so I ran it as root in the shell ](*,) 
Now, when I try to run Firefox I get this error message:

> Cannot launch icon

Details: Failed to execute child process "firefox" (Permission denied)

Likewise from the application menu.
I tried completely removing Firefox via Synaptic, but that didn't help.

I suspect the solution lies in moving back the firefox symlink and restoring the original /usr/bin/firefox script. Do you know how to do the first? And does anyone have a script for me? Or do you know what else I should do? :-? 

Thanks!

---

### Post by Malta Soron on 2006-08-15
For those interested: I solved it. Since I installed Firefox with Automatix, I just uninstalled with with the information from the relevant Automatix thread and reinstalled it and now it's working again :D

---

