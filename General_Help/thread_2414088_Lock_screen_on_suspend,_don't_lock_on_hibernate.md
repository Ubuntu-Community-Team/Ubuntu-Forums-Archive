---
title: "Lock screen on suspend, don't lock on hibernate?"
date: 2019-03-05
forum: General Help
---

### Post by fmstrat2 on 2019-03-05
Hi everyone,

I have a question about customizing the lock behavior between suspend and hibernate. I'm running 18.04, and looking to create this scenario:


[LIST=1]
[*]Close the lid 
[*]Laptop goes into s2idle (suspend, this model doesn't support s3) 
[*]1 hour passes 
[*]Open the lid 
[*]Laptop is locked, requires login 
[/LIST]
 
And also support:


[LIST=1]
[*]Close the lid 
[*]Laptop goes into s2idle 
[*]4 hours passes 
[*]Laptop goes into hibernate 
[*]Open the lid 
[*]Boots to GRUB, password is required for decryption 
[*]Laptop is not locked and already logged in 
[/LIST]

This is to remove the need to type two passwords after hibernation (encryption and GNOME login).

I've been able to get part of the way there by:
[LIST]
[*]Use ACPID to set the to run [COLOR=#008000][FONT=courier new]pm-hibernate[/FONT][/COLOR], which doesn't require a GNOME login because it runs at the system level 
[*]Use GNOME to auto-lock on suspend and the lid close action to suspend 
[/LIST]

This works, but it doesn't allow me to go to hibernate after 4 hours without a locked GNOME. Using the classic method of [https://askubuntu.com/questions/12383/how-to-go-automatically-from-suspend-into-hibernate](https://askubuntu.com/questions/12383/how-to-go-automatically-from-suspend-into-hibernate) doesn't work for me because of the dual password requirement.

So, the questions:
[LIST=1]
[*]Is there a way to have ACPID hibernate when in s2idle after a period of time? 
[*]Is there an equivilant to [COLOR=#008000][FONT=courier new]gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend false[/FONT][/COLOR] that only works for hibernation? 
[/LIST]

---

### Post by fmstrat2 on 2019-03-05
Hmm... I wonder if there is a pre/post way using /lib/systemd/system-sleep/ where I can change the ubuntu-lock-on-suspend before/after hibernation.

---

### Post by fmstrat2 on 2019-03-05
Unfortunately my attempt to do the above did not work. I created this:

/lib/systemd/system-sleep/toggle-lock
```
#!/bin/sh
set -e

if [ "$2" = "hibernate" ]; then
    case "$1" in
        pre)
            XINPUTUSER=$(who | grep :0 | sed 's/\([a-z]*\).*/\1/')
            DISPLAY=:0.0 su - $XINPUTUSER -c "gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend false"
            ;;
        post)
            XINPUTUSER=$(who | grep :0 | sed 's/\([a-z]*\).*/\1/')
            DISPLAY=:0.0 su - $XINPUTUSER -c "gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend true"
            ;;
    esac
fi
```

But the setting appears to be taken into account prior to the PRE statement.

---

