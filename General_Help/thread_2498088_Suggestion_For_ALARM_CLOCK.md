---
title: "Suggestion For ALARM CLOCK?"
date: 2024-05-30
forum: General Help
---

### Post by rebeltaz on 2024-05-30
Does anyone have a suggestion for an alarm clock for linux? Everything I have found is only for daily/weekly alarms. I need something that will sound an alarm at a specific time on a specific day. I have tried searching and I am tired of looking. I'm hoping someone will know JUST what I need. Thanks.

---

### Post by currentshaft on 2024-05-30
hd86w

---

### Post by rebeltaz on 2024-06-01
> **currentshaft said:**
> This one looks actively maintained and feature-full: [https://alarm-clock-applet.github.io/#features](https://alarm-clock-applet.github.io/#features)

Looks like it's in apt to install directly for you to try.

I swear I replied to this... ¯\_(&#12484;)_/¯
 
That was one of the ones that I had tried. Unless I am missing it, I only see a way to set daily/weekly alarms. I need something that will allow me to set an alarm for a specific time on a specific date. 

I appreciate it, though.

---

### Post by HermanAB on 2024-06-01
Note that if your computer suspends, the alarm won’t work.

---

### Post by dragonfly41 on 2024-06-01
Curiosity. I was able to knock together a prototype using Actiona UI emulator drawing on this information to drive sound/screen flashing in Settings.

[https://help.ubuntu.com/stable/ubuntu-help/a11y-visualalert.html.en](https://help.ubuntu.com/stable/ubuntu-help/a11y-visualalert.html.en)

---

### Post by rebeltaz on 2024-06-01
> **HermanAB said:**
> Note that if your computer suspends, the alarm won&#8217;t work.

Oh, yeah... I know. This computer that I want to run this on stays up 24/7.

---

### Post by Holger_Gehrke on 2024-06-01
Might the old 'at' command line tool be helpful ? It expects a command on standard input and executes that command at the time (and date) given on the command line, e.g.
```

echo "notify-send 'Hello'"|at now + 1 minute

```
will show a notification after 1 minute. You can basically run anything using 'at' but you may have to pass in a DISPLAY variable if you're running a graphical program, e.g.
```

echo DISPLAY=:0.0 xlogo | at 13:00 02.06.2025

```
will run the old xlogo at 1 pm next year on June 2nd.

Holger

---

### Post by rebeltaz on 2024-06-01
> **Holger_Gehrke said:**
> Might the old 'at' command line tool be helpful ? It expects a command on standard input and executes that command at the time (and date) given on the command line, e.g.


It's clunky, but... I like clunky :D Yeah, I think I can make that work. I tried it by passing 'vlc alarm.mp3' to it and it seemed to work great. I'm still going to keep looking for a GUI but this is awesome. I really appreciate it!

btw - I like that the "at" command will take "teatime" as a variable :lol:

---

### Post by rebeltaz on 2024-06-05
> **Holger_Gehrke said:**
> Might the old 'at' command line tool be helpful ? It expects a command on standard input and executes that command at the time (and date) given on the command line, e.g.
```

echo "notify-send 'Hello'"|at now + 1 minute

```
will show a notification after 1 minute. You can basically run anything using 'at' but you may have to pass in a DISPLAY variable if you're running a graphical program, e.g.
```

echo DISPLAY=:0.0 xlogo | at 13:00 02.06.2025

```
will run the old xlogo at 1 pm next year on June 2nd.

Holger

CRAP! I didn't notice that linux is apparently British! I didn't put the numeric date (02.06.2025) with what you said (June 2nd). I'm glad I caught that before I missed my event!

---

### Post by Holger_Gehrke on 2024-06-05
> **rebeltaz said:**
> CRAP! I didn't notice that linux is apparently British! I didn't put the numeric date (02.06.2025) with what you said (June 2nd). I'm glad I caught that before I missed my event!
I **really** hope that's a joke with seriously deadpan delivery. In case it isn't: 'at' takes 'a  date  of  the  form  MMDD[CC]YY, MM/DD/[CC]YY,  DD.MM.[CC]YY or [CC]YY-MM-DD' (from 'man at'). So it's the separator characters which at uses as a hint towards the format of the date (no separators or slashes -> American format; periods -> European format; dashes -> ISO).

Holger

---

### Post by TheFu on 2024-06-05
This has always bothered me too.

A computer always knows the time, but there isn't an excellent alarm/reminder system built in?  In the 1990s, we used "**plan**" - that's more like what we'd think of as a "Calendar" tool today. Not good for sub-15 minute reminders.  I use a calendar for that stuff - centralized using a calendar server across all my devices.

For shorter things - like a cooking timer, I used alarm-clock-applet until it broke with 20.04. Don't know why.  I ended up writing my own script.  It is far from perfect, but here is is:
```
#!/bin/bash

ALARM_FILE=/usr/share/sounds/ubuntu/ringtones/Alarm_clock.ogg
mytime="$1"

if [[ "X" = "X${1}" ]] ; then
  echo "Usage: $0 {timespec} 
   $0  1h
   $0 15m
  Enter the {timespec}: "
  read mytime
  if [[ "X" = "X${mytime}" ]] ; then
    exit 1;
  fi
fi
DATE=$(date)
echo "Timer set for ${mytime}"
echo "Started at: ${DATE}"
echo "PRESS <cntl>-c to stop alarm ..."
sleep "${mytime}" 
echo "ALARM!"
while ( true ) ; do
    mpv --no-audio-display --vo=null --volume=60 "${ALARM_FILE}"
    date
    echo "Started at ${DATE}"
    # read 1 character, use the variable "$stop" and 
    # timout after .1 seconds so the loop continues
    stop = $(read -n 1 -t 1 -s)
    if [ $? -gt 128 ] ; then
      echo "Stopping ..." 
      echo "Started at ${DATE}"
      exit 0;
    fi 
  echo "Started at ${DATE}"
done
echo "Done."
```
It has a few bugs, but none that break the alarm.  When the alarm starts, use <cntl>-c to stop it.  **sleep**  supports s, m, h, ... modifiers.  "seconds" is assumed if no modifier is provided.  I have a few preset times in a menu for quick choices.
e.g.
```
$ ./timer  10s   # Seconds

$ ./timer  20m   # Minutes

$ ./timer  1.75h   # Hours 
```

I use **mpv** as my player. Use whatever player you like.  Don't assume the audio file I use exists on your box.

BTW, 
```
sh: 71: notify-send: not found
```
must be some GUI thing?

---

### Post by rebeltaz on 2024-06-05
> **Holger_Gehrke said:**
> I **really** hope that's a joke with seriously deadpan delivery. In case it isn't: 'at' takes 'a  date  of  the  form  MMDD[CC]YY, MM/DD/[CC]YY,  DD.MM.[CC]YY or [CC]YY-MM-DD' (from 'man at'). So it's the separator characters which at uses as a hint towards the format of the date (no separators or slashes -> American format; periods -> European format; dashes -> ISO).

Holger

lol... well, the "linux being British" was a joke, but no... I honestly didn't realize the difference. I have seen American dates written using dot or dash separators before. I wasn't aware that the separators indicated a specific regional format. 

I did look at the at man before I used it, but I guess I overlooked the date formatting.

---

### Post by rebeltaz on 2024-06-05
I wrote a very similar script to use as a simple countdown timer, but I had no idea how to make it work as a date timer. My scripting knowledge is basic at best. I'll give that a try. Thank you.

---

