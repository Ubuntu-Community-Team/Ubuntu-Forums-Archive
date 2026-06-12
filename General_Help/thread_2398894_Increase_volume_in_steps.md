---
title: "Increase volume in steps"
date: 2018-08-18
forum: General Help
---

### Post by raleigh3 on 2018-08-18
I would like to modify this so the buzzer starts at 15% and goes up to 30% in volume while buzzer is sounding.
```

 amixer -D pulse sset Master 30% > /dev/null 2>&1
 cvlc --play-and-exit /usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3 > /dev/null 2>&1
 echo 'TIME IS UP.'
gxmessage -fg blue -font  'sans 20' -timeout 2 ' TIME IS UP !!'
```

---

### Post by again? on 2018-08-19
```
#!/bin/bash

soundfile="/usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3"
originalVolume=$(amixer -D pulse get Master | grep -m 1 -o -E [[:digit:]]+%)

{
    for ((volume = 15; volume <= 30; volume += 1)); do
        amixer -D pulse sset Master ${volume}% > /dev/null
        sleep 1
    done
} &

cvlc --play-and-exit "$soundfile" > /dev/null 2>&1
echo 'TIME IS UP.'
gxmessage -fg blue -font  'sans 20' -timeout 2 ' TIME IS UP !!'

#set back to original volume
amixer -D pulse sset Master $originalVolume > /dev/null
```

If your sound file is less than 15secs decrease the sleep value... eg sleep 0.5 or use
the cvlc **--input-repeat** flag to increase the playtime.
After cvlc exits, the last line in the script sets your volume back to original level.

---

