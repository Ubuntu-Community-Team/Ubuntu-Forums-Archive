---
title: "Autostart shellscript in *visible* terminal window?"
date: 2013-05-16
forum: General Help
---

### Post by wrybread on 2013-05-16
I'm setting up a Lubuntu laptop to automatically play a shoutcast stream in mplayer from terminal. For various reasons we need to watch mplayer's status window, just as if we had run it from terminal. 

Can anyone recommend a method to run the shellscript in a visible terminal (or whatever) window, at startup?

Thanks for any help.

And fyi, here's the sort of script I'm running, in case it matters:

```
while:
do
   mplayer http://goodradio.org/stream/wfmu
done
```

And on my Lubuntu install, I'm currently autorunning it by editing this file:

/etc/xdg/lxsession/Lubuntu/autostart

---

### Post by erind on 2013-05-16
I'd do it differently:  Just start a *xterm* window with *mplayer* running inside of it. Place this script in the Lubuntu's autostart file and do a [I]chmod 750 play_wfmu_radio.
[/I]
**play_wfmu_radio **

```
#!/bin/bash

## sleep 5 && xterm -T 'WFMU Radio' -hold -e mplayer http://goodradio.org/stream/wfmu

sleep 5 && xterm -T 'WFMU Radio' -e 'mplayer http://goodradio.org/stream/wfmu ; bash'

```

You can even start the window minimized if you want, say using *gdevilspie*. The script is tested on Xubuntu, but shoudn't be any issues on Lubuntu.

---

### Post by wrybread on 2013-05-16
Works beautifully, thanks.

To anyone else coming this way:

I needed to run a loop so it would keep trying to play the station even if I lost the connection or they stopped streaming for a moment, so I wound up making two files: "radio1" has my script (printed in my original post) and a second file (radio2) with:

```
#!/bin/bash

sleep 5 && xterm -T 'Radio' -e '/home/me/Desktop/radio1; bash'

```

And my autostart file (in lubuntu, that's /etc/xdg/lxsession/Lubuntu/autostart) runs radio1.

I'm guessing there's a way to put the contents of radio1 (the while loop) directly into an xterm command (radio2), and furthermore to put it all in my my autostart file, but this works.

---

### Post by erind on 2013-05-16
> **wrybread said:**
> Works beautifully, thanks.

[...]

I'm guessing there's a way to put the contents of radio1 (the while loop) directly into an xterm command (radio2), and furthermore to put it all in my my autostart file, but this works.

Try this:

```
#!/bin/bash
#set -x

sleep 5
while :
do
 xterm -T 'WFMU Radio' -e mplayer http://goodradio.org/stream/wfmu 
done

## To run the loop inside xterm uncomment the line below, and comment out the whole loop above.
## xterm -T 'WFMU Radio' -e 'while : ; do mplayer http://goodradio.org/stream/wfmu ; done' 
```

---

### Post by wrybread on 2013-05-16
Thoroughly awesome, thanks, working beautifully and much more efficiently now.

---

