---
title: "close instead of minimising to tray"
date: 2019-07-23
forum: General Help
---

### Post by barrymmm on 2019-07-23
This is a small but very irritating issue for me. I have Viber installed on my machine and when I hit the X button it just minimises to the tray. Unlike other programs that do this, I cannot seem to find anything in Vibers settings to change this behaviour. This means that I have to right click it on the tray and hit close or hit Alt+F4. Definitely a first world problem I know but it irritates the **** out of me.
Is there some way I can override this setting either in Viber itself or system wide so that any time I hit the X button in any program, it behaves like the X button has behaved on all GUI's since the 1990's and closes the ****ing program?

---

### Post by #&amp;thj^% on 2019-07-23
Install wmctrl and use the following script or tweak to your liking.
I use this startup script:
```

#!/bin/bash
set -e

export QT_AUTO_SCREEN_SCALE_FACTOR=0
/opt/viber/Viber StartMinimized &

while ! wmctrl -xc Viber.ViberPC; do
    sleep .5
done

```
Here is the Details:
[list]
    [*]export QT_AUTO_SCREEN_SCALE_FACTOR=0 to avoiding huge display on my XFCE4
    [*]Viber StartMinimized to starting Viber hidden as possible
    [*]**_wmctrl -xc Viber.ViberPC_** to closing the Viber window only avoid closing others
    [*]while ! wmctrl ... to close the windows as fast it can
[/list]
Now if you don't want Viper to start on login, remove "/opt/viber/Viber StartMinimized"

---

