---
title: "I've got side mouse buttons, but I lost USB flash stick!"
date: 2007-02-26
forum: General Help
---

### Post by Tosa on 2007-02-26
I'm definitely getting frustrated...
I was trying to make side mouse buttons work again... They did before I had to reinstall Kubuntu (that's the origin of my frustration), but I couldn't remember what I've done. Finally, after putting this to xorg.conf and a reboot
> #    Identifier    "Configured Mouse"
#    Driver        "evdev"
#    Option        "CorePointer"
#    Option        "Dev Name"    "A4Tech PS/2+USB Mouse"
#    Option        "Dev Phys"    "usb-0000:00:02.1-2/input0"
#    Option        "Device"    "/dev/input/event3"
#    Option        "Buttons"    "9"
#    Option        "ZAxisMapping"    "4 5"

side buttons worked! But the middle button scrawl didn't. Then I discovered that my USB flash was gone. I reinserted it but nothing happened.
So I rebooted again, hoping that things would sort out themselves. Was I wrong! It's not that I didn't have Usb flash (still inserted), but the mouse was gone too! I managed to put this
    > Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ExplorerPS/2"
    Option        "Buttons" "7"
    Option        "ZAxisMapping" "4 5"
    Option        "ButtonMapping" "1 2 3 6 7"
    Option        "Emulate3Buttons"    "true"
into the xorg.conf and the mouse was back together with side buttons! Funny thing is that I've put those lines before, but they didn't work.
Now, the problem is that I still don't have my USB flash stick. I've tried inserting and reinserting it several times, but its not detected... How do I get it back?

---

