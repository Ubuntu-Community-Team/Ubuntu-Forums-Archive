---
title: "Run script on suspend/resume"
date: 2017-02-28
forum: General Help
---

### Post by fernando-j-ferreira on 2017-02-28
Hello there.

I'm trying to run custom scripts on  suspend / resume in 16.04 LTS to auto disconnect / reconnect bluetooth audio  and disable / reenable pulseaudio-equalizer as not killing it will screw the bluetooth adapter.

For that I've written a very small script lying in /lib/systemd/system-sleep/ named 00blueaudio_switch with following contents.

```
#!/bin/sh
if [ $1 = post ] && [ $2 = suspend ]
then /home/fernando/bin/blueaudio-on.sh
elif [ $1 = pre ] && [ $2 = suspend ]
then /home/fernando/bin/blueaudio-off.sh
fi
```[COLOR=#000000]
The suspend (blueaudio-off.sh) script is always executed independently of being placed after "if" or after "elif" but the resume script never runs independently of its contents. It simply does not get executed.

Why? What am I doing wrong here?
[/COLOR]
Can anyone kindly help me with this?
[COLOR=#000000]
[/COLOR]

---

### Post by u2nTu on 2017-04-29
Don't know if this will work for you, but using the structure of wpasupplicant:

```
#!/bin/sh
set -e

if [ "$2" = "suspend" ] || [ "$2" = "hybrid-sleep" ]; then
    case "$1" in
        pre) /home/fernando/bin/blueaudio-off.sh ;;
        post) /home/fernando/bin/blueaudio-on.sh ;;
    esac
fi

```

Your logic does mostly the same thing, but note the few differences, one or more of which may be the key to make it run.

Was doing a driveby when I found your post, hth.

---

