---
title: "Ubuntu 20.04 LTS Make Headphones Work (full script inc)"
date: 2023-03-10
forum: General Help
---

### Post by xinuzi on 2023-03-10
Hi,

After a few updates, I only recently discovered that my headphones were working but not giving any sound anylonger on my (L)Ubuntu 20.04 LTS.
 Absolutely the Best Solution seemed to be this tiny code ```
alsactl restore
```

Processed in a clickable bash script (make executable, keep at hand, possibly copy to Desktop):

```
#!/bin/bash

clear

TITLE="HEADPHONES ON"
echo -en "\033]0;$TITLE\a" # Window title

echo "$TITLE"

echo

echo "Reset alsa in order to hear headphones..."

echo

alsactl restore

echo

sleep 1

echo "Done."

echo

echo "Window closes automatically in 3 seconds..."

sleep 3

exit

read
```

As I've heard the issue doesn't occur anymore in a later Ubuntu version.
Alsa, Pulse - things can become mixed up.

---

### Post by xinuzi on 2023-03-28
No headphone struggles indeed in (L)Ubuntu 22.04 .

Alsamixer vs pulse audio, things can be confusing but when one looks better the settings are there, also gui-wise. ;-)

Like these settings, when you rightclick the taskbar sound-icon (as it shows in Lubuntu):

 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=291973&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291974&stc=1[/IMG]

('ingebouwde analoge stereo' = 'analogue stereo')
(Image 1 shows a locked panel. Unlock to set.)

This setting makes the sound icon in the taskbar work well.
Extra settings of the sound(s) by clicking the sound taskbar/panel sound-button and then 'Mixer'.

Volume/sound configurations to keep an eye on, are the analogue (pc) setting vs the hdmi setting.

Tothelooo.

---

