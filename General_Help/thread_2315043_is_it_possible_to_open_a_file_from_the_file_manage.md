---
title: "is it possible to open a file from the file manager with a program run from a script?"
date: 2016-02-25
forum: General Help
---

### Post by nargaroth_reg on 2016-02-25
[COLOR=#111111][FONT=Ubuntu]I've created some scripts to run google chrome and other applications on ubuntu 14.04 using certain arguments.
 The problem is that when the program is executed for instance by double clicking a .html file in the file manager or in another application the default version of it is executed, not as specified in my script. I tried setting the custom script as the default command to be run when opening that kind of file, but then the program is run without opening the particular file, adding %u, %f, etc. to the exec line of a .desktop of the script didn't help either.
[[IMG]http://s18.postimg.org/i426hf3id/dsa.jpg[/IMG]]("http://postimg.org/image/i426hf3id/")


This is the one I use with google chrome for example:[/FONT][/COLOR]
```

#!/bin/sh
xset -dpms
google-chrome-stable --force-device-scale-factor=1 --password-store=basic --window-position=318,0
tvt=$(pgrep -c "tvtime")
vlc=$(pgrep -c "vlc")
if [ "$tvt" -eq 0 ] && [ "$vlc" -eq 0 ] ; then
  xset dpms 0 600 0
fi

```
[COLOR=#111111][FONT=Ubuntu]
Any ideas on what could I try to get the program to open the specific file selected in the file manager/other application?[/FONT][/COLOR]

---

### Post by nargaroth_reg on 2016-02-26
I've found a workaround for this issue. I'm now using [https://github.com/kodx/lightsOn](https://github.com/kodx/lightsOn) to handle dpms and I'm setting the options for chrome in it's .desktop file in /.local/share/applications

---

