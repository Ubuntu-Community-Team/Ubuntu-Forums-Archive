---
title: "How to disable screen blanking ?"
date: 2019-06-01
forum: General Help
---

### Post by linuxyogi on 2019-06-01
Hi,

I did

```
Menu > Preferences > Power Manager >Display>Display power management >OFF
Menu > Preferences > Power Manager >Security>Automatically Lock Screen>Never
```

but still the display turns off after some minutes of inactivity

How can I stop this  ?

---

### Post by TheFu on 2019-06-01
I use this. YMMV.
```
#!/bin/bash

# ###########################################################
while getopts 'yn' OPTION
do
  case $OPTION in
  y)    xset s off &
        xset -dpms &
        killall xscreensaver 
        echo "Screen Blanking Disabled"
        ;;
  n)   xset +dpms &
       xset s on &
       xscreensaver-demo &
       echo "Screen Blanking Enabled"
        ;;
  esac
done
```

---

### Post by linuxyogi on 2019-06-02
> **TheFu said:**
> I use this. YMMV.
```
#!/bin/bash

# ###########################################################
while getopts 'yn' OPTION
do
  case $OPTION in
  y)    xset s off &
        xset -dpms &
        killall xscreensaver 
        echo "Screen Blanking Disabled"
        ;;
  n)   xset +dpms &
       xset s on &
       xscreensaver-demo &
       echo "Screen Blanking Enabled"
        ;;
  esac
done
```

I need to copy the above to a text file, make it executable and add it to startup ?

---

### Post by #&amp;thj^% on 2019-06-02
Thefu's script works just fine.
If you need an easier method try this:
If you want to wrap your app in a script that takes care of this for you when you launch it (or GUI simply isn't an option),
To disable the screen blackout:
```

gsettings set org.gnome.desktop.session idle-delay <seconds>** (0 to disable)**
```

To disable the screen lock:
```

gsettings set org.gnome.desktop.screensaver lock-enabled false
```

If your gui doesn't work, then you could try using **xset**

Open a terminal and type:
```

xset s off
```

To also prevent the display from blanking and to prevent the monitor's DPMS energy saver from kicking in, add the following:
```

xset s noblank
xset -dpms
```

Also you could try some things here: [https://wiki.archlinux.org/index.php/Display_Power_Management_Signaling#xset_screen-saver_control](https://wiki.archlinux.org/index.php/Display_Power_Management_Signaling#xset_screen-saver_control)

---

### Post by linuxyogi on 2019-06-02
> **1fallen said:**
>  If your gui doesn't work, then you could try using **xset**

Open a terminal and type:
```

xset s off
```

To also prevent the display from blanking and to prevent the monitor's DPMS energy saver from kicking in, add the following:
```

xset s noblank
xset -dpms
```



I have made a shell script with your commands. How do I add it to startup ?

---

### Post by #&amp;thj^% on 2019-06-02
Bear in mind I have not used Lubuntu for a number of years now but, Select "Preferences" > "Default applications for LXSession";
In the opened window, select the option "Autostart";
Now you can enable or disable the autostarted applications, check/uncheck.

---

### Post by linuxyogi on 2019-06-02
> **1fallen said:**
> Bear in mind I have not used Lubuntu for a number of years now but, Select "Preferences" > "Default applications for LXSession";
In the opened window, select the option "Autostart";
Now you can enable or disable the autostarted applications, check/uncheck.

I did 

```
Preferences > Default applications for LXSession>Autostart>Add>/home/lubuntu/noblank
```

Problem is after adding the path when I close Default applications for LXSession and launch it again the

newly added autostart item is lost.

---

### Post by #&amp;thj^% on 2019-06-02
default Lubuntu session is ~/.config/lxsession/Lubuntu/autostart
and FWIW the entry doesn't require or need the "@" prefix, just the full path to the script.
```
/home/username/scripts/start-up.sh
```
And maybe for good measure: is the script is executable
```

chmod +x /path/to/start-up.sh
```
Remember if your script needs root permissions it will not work. {Just a heads up}

---

### Post by linuxyogi on 2019-06-02
> **1fallen said:**
> default Lubuntu session is ~/.config/lxsession/Lubuntu/autostart
and FWIW the entry doesn't require or need the "@" prefix, just the full path to the script.
```
/home/username/scripts/start-up.sh
``` 

When I opened that file 

~/.config/lxsession/Lubuntu/autostart

the file was totally empty. I added the full path to the script. Now I will do a log out log in and test.


I will write back about what happens.

---

### Post by #&amp;thj^% on 2019-06-02
> **linuxyogi said:**
> 
the file was totally empty. I added the full path to the script. Now I will do a log out log in and test.


A reboot might be better for a new session. :)

---

### Post by linuxyogi on 2019-06-02
> **1fallen said:**
> A reboot might be better for a new session. :)

I just finished rebooting. I will post back.

---

### Post by #&amp;thj^% on 2019-06-02
May the Force be with you. ;)

---

### Post by linuxyogi on 2019-06-02
It didn't work. I just left the PC on and went for a walk. When I came back the screen was off (standby mode).

---

### Post by TheFu on 2019-06-02
> **linuxyogi said:**
> It didn't work. I just left the PC on and went for a walk. When I came back the screen was off (standby mode).

Standbye is a completely different issue than preventing a screen from blanking.

---

### Post by linuxyogi on 2019-06-02
> **TheFu said:**
> Standbye is a completely different issue than preventing a screen from blanking.

What happens is my monitor goes into standby mode after I leave the PC on without any activity.

What is this process called ?

How to disable it ?

When I was using openSUSE (Gnome) this issue was not there.

---

### Post by linuxyogi on 2019-06-03
```
gsettings set org.gnome.desktop.session idle-delay 0
```

This worked. Marking as solved.

---

