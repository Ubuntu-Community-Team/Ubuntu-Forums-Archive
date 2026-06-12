---
title: "Map Backspace key????"
date: 2007-01-02
forum: General Help
---

### Post by marco999 on 2007-01-02
How do I map a button on my mouse to the backspace key??????

I tried to follow this how to but it was kinda hard to understand
[http://www.ubuntuforums.org/showthread.php?t=316441&highlight=lomoco]("http://www.ubuntuforums.org/showthread.php?t=316441&highlight=lomoco")


Can someone please tell me what the syntax would be to do this??????


marco999

---

### Post by icouldntfindausername on 2008-07-22
I'm revieving this thread as I'm wondering about the same thing. In firefox it works as it should, but in opera and nautilus it doesn't. However, using backspace on my keyboard works, so mapping the mouse button to backspace would probably work. I only need to know how... :confused:

Here's the relevant section of my xorg.conf file:
```
Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 8"
    Option         "ZAxisMapping" "4 5"
EndSection
```

Cheers. :)

---

