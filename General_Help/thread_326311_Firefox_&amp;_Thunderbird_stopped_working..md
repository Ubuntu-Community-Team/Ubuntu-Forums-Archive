---
title: "Firefox &amp; Thunderbird stopped working."
date: 2006-12-27
forum: General Help
---

### Post by angrykeyboarder on 2006-12-27
[This is on Edgy i386, btw]

I'm sure it has to do with some other unofficial packages I installed* as it was after that they they stopped working.

I've since uninstalled Firefox and Thunderbird completely (i.e. purged) as well as a number of packages that they depend on. *Then I reinstalled Firefox and Thunderbird as well as their dependencies and nothing changed.

Before and after I did the uninstall/reinstall I would get no response when clicking on their respective icons.

Then I tried launching from within a terminal. Nothing. *The respone would be nothing but a new bash prompt.

I find this all rather odd.

Outside of wiping the slate clean and starting fresh with a new Ubuntu
install, does anyone have any other suggestions as to how I might get
Firefox and Thunderbird working again?

Thanks




[SIZE="1"]*Yes, I screwed up. Yes I should have known better. No lectures please,
thanks.[/SIZE]

---

### Post by cilynx on 2006-12-27
Did you make sure that you didn't have any running / zombie copies before trying to spawn from the terminal?  If there's a dead copy running in the background, you generally get back nothing but another prompt.  If it launched and died, you generally get something maybe sorta moderately useful back.  Just a thought...

---

### Post by TLE on 2007-01-08
I just got this exact problem. I have experienced it once before but I never learned what solved it back then, but now it's there again. As the original reporter writes, the last time I tried reinstalling alot of things and removing all plugins and userfolders and nothing helped.

I have attached the output of running the apps with sh -x if that can help anybody figure this out.
\TLE

---

### Post by cilynx on 2007-01-08
Not sure if you'll be able to extrapolate this out to your original problem, but there is a problem with doing 
```

sh -x /usr/bin/firefox

```
In Edgy, the default shell (sh) is dash, not bash.  /usr/bin/firefox is a bash script.  If you force it to run with dash, you get the syntax error as you described.  Try:
```

bash -x /usr/bin/firefox

```
and let us know how that goes...

This is the output on my (working) system

With Dash (the default):
```

rcw@angus:~$ sh -x /usr/bin/firefox 
+ [  ]
+ MOZ_DIST_BIN=/usr/lib/firefox
+ MOZ_PROGRAM=/usr/lib/firefox/firefox-bin
+ RUNTIME_FIREFOX_DSP=
+ [ -f /etc/firefox/firefoxrc ]
+ . /etc/firefox/firefoxrc
+ FIREFOX_DSP=none
+ [ -f /home/rcw/.mozilla/firefox/rc ]
+ [ -f /home/rcw/.mozilla-firefoxrc ]
+ [ x = x ]
+ egrep ^(bn|gu|hi|kn|ml|mr|ne|pa|si|ta|te)_ /var/lib/locales/supported.d/*[^~]
+ MOZ_DISABLE_PANGO=1
+ export MOZ_DISABLE_PANGO
+ [ x1 = x0 ]
+ [  ]
+ [ -z none ]
+ [ none = auto ]
+ [ none = none ]
+ FIREFOX_DSP=
+ EXTENT_LD_LIB_PATH=/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins
+ [  ]
+ LD_LIBRARY_PATH=/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins
+ LD_LIBRARY_PATH=/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins:
/usr/bin/firefox: 121: Syntax error: Bad substitution
rcw@angus:~$ 

```
That's it, no window spawned

Specifing Bash (what ff needs)
```

rcw@angus:~$ bash -x /usr/bin/firefox 
+ '[' '' ']'
+ MOZ_DIST_BIN=/usr/lib/firefox
+ MOZ_PROGRAM=/usr/lib/firefox/firefox-bin
+ RUNTIME_FIREFOX_DSP=
+ '[' -f /etc/firefox/firefoxrc ']'
+ . /etc/firefox/firefoxrc
++ FIREFOX_DSP=none
+ '[' -f /home/rcw/.mozilla/firefox/rc ']'
+ '[' -f /home/rcw/.mozilla-firefoxrc ']'
+ '[' x = x ']'
+ egrep '^(bn|gu|hi|kn|ml|mr|ne|pa|si|ta|te)_' /var/lib/locales/supported.d/en /var/lib/locales/supported.d/local
+ MOZ_DISABLE_PANGO=1
+ export MOZ_DISABLE_PANGO
+ '[' x1 = x0 ']'
+ '[' '' ']'
+ '[' -z none ']'
+ '[' none = auto ']'
+ '[' none = none ']'
+ FIREFOX_DSP=
+ EXTENT_LD_LIB_PATH=/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins
+ '[' '' ']'
+ LD_LIBRARY_PATH=/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins
+ LD_LIBRARY_PATH=/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins:
+ LD_LIBRARY_PATH=/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins:
+ LD_LIBRARY_PATH=/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins
+ export LD_LIBRARY_PATH
+ MOZ_PLUGIN_PATH=/usr/lib/mozilla-firefox/plugins
+ export MOZ_PLUGIN_PATH
+ APPLICATION_ID=firefox
+ VERBOSE=
+ DEBUG=0
+ DEBUGGER=
+ first=1
+ opt=
+ set -a firefox
+ '[' 1 -ne 0 ']'
+ shift
+ OPTIONS=
+ '[' 0 -eq 1 ']'
+ echo_vars FIREFOX_DSP APPLICATION_ID CMDLINE_DISPLAY DISPLAY OPTIONS DEBUG DEBUGGER MOZ_DISABLE_PANGO MOZ_NO_REMOTE
+ '[' '' ']'
+ type ''
+ exec_verbose /usr/lib/firefox/firefox-bin
+ verbose Running: /usr/lib/firefox/firefox-bin
+ '[' '' ']'
+ exec /usr/lib/firefox/firefox-bin
rcw@angus:~$ 

```
it then spawns the window.

---

### Post by TLE on 2007-01-08
Oh yeah right. bash, dash, sh. Anyway my problem went away. It's i little concerning. Thanks for the help anyway.

---

