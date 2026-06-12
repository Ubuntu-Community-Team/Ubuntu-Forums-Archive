---
title: "strange script behaviour"
date: 2013-05-22
forum: General Help
---

### Post by HiImTye on 2013-05-22
background: I have my main box running as a headless server while we are staying with family for the summer, which I SSH to if I need to use RDP or do anything other than use MPD, Samba, DLNA, or Deluged. 

issue: I'm experiencing some odd behaviour with a shell script, which I'm using to convrrt some videos with ffmpeg. it runs fine if I don't specify a framerate or flags in advance. the issue is, that the '-z' test is reporting the variable empty even though it isn't, as seen here:[IMG]http://imageshack.us/a/img842/8902/screenshot2013052214232.png[/IMG]
here's the script:
```

#!/bin/bash
# new file name
if [ -z "$rate" ]; then
 rate="29.985"
fi
echo rate="$rate"

if [ -z "$flags" ]; then
 flags="+aic+mv4"
fi
echo flags="$flags"

F="converted/${1%.*}.mp4"
if [ ! -d "converted" ]; then
 mkdir converted
fi

if [ ! -f "$F" ]; then    
 ffmpeg -i "$1" -r "$rate" -acodec libvo_aacenc -b 128k -vcodec mpeg4 -b 1200k -flags "$flags" "$F"
fi

```

---

### Post by schragge on 2013-05-22
If you don't export the variable, the script doesn't see it. Invoke it as
```
rate=25 avi2mp4 test
```

---

### Post by HiImTye on 2013-05-22
thanks, I did thst before when I had the test inverted and it didn't work (for obvious reasons), and I had forgotten jntil just now. /embarassed

edit: the new way to solve threads is a pain lol
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

