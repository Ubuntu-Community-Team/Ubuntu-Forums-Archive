---
title: "bucklespring.buckle: command not found"
date: 2019-07-19
forum: General Help
---

### Post by ardouronerous on 2019-07-19
Running Lubuntu 18.04.

I've installed bucklespring via Synaptic Package Manager, but when I try to run [FONT=courier new]bucklespring.buckle[/FONT] on the terminal, I get this error:

```
bucklespring.buckle: command not found
```

---

### Post by again? on 2019-07-19
Where did you get that command from?
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] buckle -h**

bucklespring version 1.4.0
usage: buckle [options]

options:

  -d DEVICE use OpenAL audio device DEVICE
  -f        use a fallback sound for unknown keys
  -g GAIN   set playback gain [0..100]
  -m CODE   use CODE as mute key (default 0x46 for scroll lock)
  -h        show help
  -l        list available openAL audio devices
  -p PATH   load .wav files from directory PATH
  -s WIDTH  set stereo width [0..100]
  -v        increase verbosity / debugging
```
Try ...
```
buckle -f
```

FYI bucklespring installs to /usr/games/buckle...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] dpkg -L bucklespring**
/.
/usr
/usr/games
/usr/games/buckle
/usr/share
/usr/share/doc
/usr/share/doc/bucklespring
/usr/share/doc/bucklespring/changelog.Debian.gz
/usr/share/doc/bucklespring/copyright
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/bucklespring
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/buckle.1.gz
```

---

### Post by ardouronerous on 2019-07-19
Thanks, that's worked.

I got the command off this: [URL="https://itsfoss.com/buckle-spring-keyboard-sound-linux/"]https://itsfoss.com/buckle-spring-keyboard-sound-linux/

[/URL]How do I get it stop though?

---

### Post by ardouronerous on 2019-07-19
I got it: Ctrl+C

---

### Post by again? on 2019-07-19
I used buckle for a while and quite liked it.
Just add **buckle -f** to startup applications.
To stop run..
```
pkill buckle
```

or use this script set to keyboard shortcut to toggle on off.
_buckle-toggle.sh_
```
#!/bin/bash

if (pidof buckle) 
	then
		killall buckle
	else
		buckle -f &
fi
exit 0
```

---

