---
title: "Any way to change system theme when on battery?"
date: 2008-07-01
forum: General Help
---

### Post by one_man_down on 2008-07-01
Not sure if this is the right subforum to ask, so feel free to move this.

First, let me give some background information.

I am running Xubuntu 7.10 on my Thinkpad 600E.

I have been using linux, primarily Ubuntu, as my main OS for the past 2 years and am not adverse to tinkering behind the scenes with config files, scripting compiling and the like if needed.

My system theme is normally set to Xfce-dusk to reduce eyestrain, but since it is a black theme it drains the battery much more quickly when i'm mobile, and  is less tolerant of glare caused by the sun and etc when outside.

I have been manualy changing the theme to Xfce-dawn when i go on battery and back to fce-dusk when on AC.

To get to the point, i was wondering if there was a way to automate the theme switch when ac power is removed.

To me this would entail 3 things:

1. Some way of seeing the power state of the system.
2. Some way of running a command or shell script when switching from AC to battery and a different script or command when switching back.
3. A way to change the system theme from the command line.

I think the battery state and etc is sent out over dbus, but i'm not sure if it is, or how to accses it if it is.

I also have yet to find a command line way to swap themes with Xfce.

I tried the almighty google but didn't find anything similar to this.

Any help would be greatly apreciated, and thanks in advance!

EDIT: Right after posting this I found out that you can query whether AC is present or not by checking for the presence of on_ac_power in bash, so that takes care of one and 2, leaving only the command line way to change themes.

This is the small test script i have so far.


```
#!/bin/bash

while true; do
if on_ac_power; then
echo "AC"
while true; do
if ! on_ac_power; then
echo "Battery"
break
fi
sleep 2
done
fi
sleep 2;
done

```

---

