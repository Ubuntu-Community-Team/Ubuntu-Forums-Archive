---
title: "Bash Help required for Suspend conditions"
date: 2014-06-10
forum: General Help
---

### Post by soumoks on 2014-06-10
Hi ,
I am currently using this script mapped to a keyboard shortcut to suspend my system.
```

#!/bin/sh 
gnome-screensaver-command --lock
dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend

```
The script however fails to work when the screen is already in a lock state. Is there a loop which I can add to check for system lock and if found true then execute the suspend command? 

Thank you.

---

### Post by Toz on 2014-06-10
If I'm understanding correctly....

```
while true
do
[[ $(gnome-screensaver-command -q | grep " active") ]] && dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
sleep 2s
done
```

"gnome-screensaver-command -q" returns the current state of the screensaver (avtive or inactive). The command above tests to see of the response is active and if so, executes the suspend command. I've also add a sleep timer to wait for 2 seconds so that the script pauses for a bit (because it runs continuously) - adjust to your liking.

However, this isn't really a script you would add to a shortcut key because it does run continuously and the shortcut key would only create another instance of the script. It is better if it is run only once.

---

### Post by soumoks on 2014-06-10
Can this be done,thus eliminating the while loop altogether?
```

#!/bin/sh 
if [ $(gnome-screensaver-command -q | grep " active")  ]; then 
  dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend


else
  gnome-screensaver-command --lock
  dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
fi

```

However when I run the above script when system is unlocked, only the screen switched off(didn't supend I presume) forcing me to perform a hard reboot,can you point out where I'm going wrong.
Thanks again.

---

### Post by Toz on 2014-06-10
Try with double square brackets:
```
#!/bin/sh 
if [[ $(gnome-screensaver-command -q | grep " active") ]]; then 
  dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
else
  gnome-screensaver-command --lock
  dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
fi
```

---

