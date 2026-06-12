---
title: "Firefox execution link wrecked"
date: 2006-08-10
forum: General Help
---

### Post by Malta Soron on 2006-08-10
Hi everyone,

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

I didn't know what to do with the last line, so I ran it as root in the shell.
Now, when I try to run Firefox I get this error message:

> Cannot launch icon

Details: Failed to execute child process "firefox" (Permission denied)

Same from the application menu.
I tried completely removing Firefox, but that didn't help. Do you know a way to solve this problem?

---

### Post by Malta Soron on 2006-08-11
I suspect the solution lies in moving back the firefox symlink and restoring the original /usr/bin/firefox script. Do you know how to do the first? And does anyone have a script for me?

---

### Post by Malta Soron on 2006-08-11
Anybody?

---

