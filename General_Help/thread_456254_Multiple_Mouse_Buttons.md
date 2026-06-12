---
title: "Multiple Mouse Buttons?"
date: 2007-05-27
forum: General Help
---

### Post by Hendrick on 2007-05-27
Hi.

I have an HP Wireless Rechargeable mouse.  It has two extra buttons.  On Windows XP, I have the one set as copy, and the other as paste.  I find myself all the time clicking them, trying to get them to do their Win XP functions.

I read this article, but I get a little lost.
[https://help.ubuntu.com/community/ManyButtonsMouseHowto?highlight=%28mouse%29](https://help.ubuntu.com/community/ManyButtonsMouseHowto?highlight=%28mouse%29)

My /etc/X11/xorg.conf looks like this:
> Section "InputDevice"
     Identifier      "Configured Mouse"
     Driver           "mouse"
     Option          "CorePointer"
     Option          "Device"                   "/dev/input/mice"
     Option          "Protocol"                 "ImPS/2"
     Option          "ZAxisMapping"        "4 5"
     Option          "Emulate3Buttons"   "true"
     Option          "Buttons"                  "7"
EndSection


Then in /etc/X11/imwheel/imwheelrc, I have absolutely no clue what to do.  I don't know where to put the code, and I don't know what the Copy and Paste command would be (It would probably have to be set to the keyboard shortcut, so pushing the button will display ctrl c).

By default the one button was pre-assigned to Right Click.  The other button isn't assigned at all.


Thanks for the help.

---

### Post by doctoss on 2007-05-27
Hey, I am trying to get my thumb button to work also. Just letting you know u are not alone out there.

---

### Post by Hendrick on 2007-05-29
Does anyone know?  I'm always finding myself click these buttons, and wondering why nothing is happening...

---

### Post by evilc on 2007-05-29
Don't know if this helps but try changing your xorg file to:
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"    "ExplorerPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
    Option        "Buttons"    "7"
    Option        "ButtonMapping" "1 2 3 6 7"

You can check what number is asigned to each button by typing in terminal "xev" (without quotes) then use box to see each button/wheel movement.
You can also look at this link [http://ubuntuforums.org/showthread.php?t=44191&highlight=mouse+buttons](http://ubuntuforums.org/showthread.php?t=44191&highlight=mouse+buttons)

---

