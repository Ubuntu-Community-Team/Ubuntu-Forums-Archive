---
title: "Can I use zenity (or similar) to show terminal output in a drop down?"
date: 2016-10-13
forum: General Help
---

### Post by CaptainMark on 2016-10-13
So I have a bash script that run a quick network based backup. Currently I have a script run, which pipes the output to zenity in order to show a basic progress meter. The script checks for failures and will throw an error message if any problems occur, again in zenity, but currently if there is an error I must open a terminal and run the commands manually in order to see what the errors are, sometimes this makes it hard for debugging the errors because they might not occur the second time around leaving me scratching my head what the problem was.

Now picture this, for those of you familiar with GParted (if you're not, essentially a GUI wrapper for a bunch of bash scripts relating to disk management) , when you run an operation, the progress bar GUI appears and shows you its doing something and just below this is a little arrow, you click the little arrow and a drop down terminal appears showing you the actual commands as they are running, useful.

Is there a way for me to do something very similar with zenity or a similar program so upon getting an error I can simply drop the terminal down and see exactly what the problem was? I could write to a log file but I'd prefer a GUI tool, the catch is, I'm not an experience programmer of any kind, I can't handle making my own UI, hence the reliance on zenity here.

The code is below, any tips would be appreciated.

Regards
Mark

```
#!/bin/bash


set -o pipefail


unison desktop-raspberry | \
    zenity --progress \
        --title="Unison Sync" \
        --text="Syncing your desktop PC to your Raspberry Pi file server" \
        --pulsate \
        --auto-close \
        --no-cancel || \
    zenity --error \
        --title="Unison Sync" \
        --text="There has been an error syncing your desktop PC with your Raspberry Pi file server, you should invesigate this error maunally"

exit 0


```

---

