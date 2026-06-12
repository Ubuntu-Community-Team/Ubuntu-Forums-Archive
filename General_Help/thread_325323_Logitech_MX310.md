---
title: "Logitech MX310"
date: 2006-12-25
forum: General Help
---

### Post by tonyisntcreative on 2006-12-25
Since Breezy I've been using a script that started with my Gnome session to get my mouse buttons working correctly.  When I upgraded to dapper it took a tiny bit of editting, but the method works wonderfully.  With what I've done I didn't need to change xorg.conf at all.
 ```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```
and the script...
```
#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

```

The mouse I've had for the past several years is a Belkin mouse with five buttons (the shoulder buttons for forward and back).  Just today I recieved a new mouse as a gift because, as I said, I've had the other one for several years.

The mouse I'm using now is a Logitech MX310.  From plugging it in the shoulder buttons worked right away as did everything else.  There is one button that doesn't do what I would like it to, though.  

Below the scroll wheel is a button that under Windows apparently switches between windows.  I'd like to set it up to do the same thing, but there is a problem.  This button is also mapped as "button 1" - the same as my left click.  Is there any way around this?

---

### Post by Vox754 on 2006-12-25
Come on! This is a hardware, programming question

[http://ubuntuforums.org/forumdisplay.php?f=135](http://ubuntuforums.org/forumdisplay.php?f=135)
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)
[http://ubuntuforums.org/search.php?searchid=11732854](http://ubuntuforums.org/search.php?searchid=11732854)

---

### Post by tonyisntcreative on 2006-12-25
Hmm...didn't really fit hardware entirely to me, and I don't think it's a programming matter, either...so I just stuck it under general.

---

