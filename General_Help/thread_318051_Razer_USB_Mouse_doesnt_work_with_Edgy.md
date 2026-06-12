---
title: "Razer USB Mouse doesnt work with Edgy"
date: 2006-12-13
forum: General Help
---

### Post by Scythe!? on 2006-12-13
Hey. I have a Razer Copperhead and it no longer works in Edgy. The actual lights on it don't light up, so the mouse does not power up. It worked fine in Dapper. Other USB Devices work fine. If i unplug it and plug it back in, it has a tiny bit of power then switches off. Any ideas?

---

### Post by hikaricore on 2006-12-13
Just curious have you tried your mouse on another computer to see if it's not just crapping out on you?  If the other USB hardware is working and this one used to work, I would always entertain the possibility that your mouse is dying until proven otherwise.

---

### Post by Scythe!? on 2006-12-13
> **hikaricore said:**
> Just curious have you tried your mouse on another computer to see if it's not just crapping out on you?  If the other USB hardware is working and this one used to work, I would always entertain the possibility that your mouse is dying until proven otherwise.
I run dual boot and it runs perfect in Windows. So no, its not breaking on me.

---

### Post by Scythe!? on 2006-12-14
Anyone? I might have to uninstall Ubuntu if i cant get it working!:cry:

---

### Post by m0ntel on 2006-12-14
i have mine working.. this is my section in xorg.conf

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "Resolution" "1600"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection

---

### Post by Scythe!? on 2006-12-21
*UPDATE* I have just tried the 6.06 Live CD and the mice doesnt work, yet it did when I installed it 6 months ago. I'm going to google around, hope the mouse isnt dying. Yet, it works perfectly with windows. :-k

UPDATE 2: It works on Edgy! But only in another port? Its absolutely dead in the original port. Because Razer's drivers in Windows requires a certain port, I will reinstall the Windows drivers and see how it goes.

---

### Post by Scythe!? on 2006-12-22
What ever usb port i use the mouse in, the mouse does not work in that slot. It seems like that slot is not getting any power, but it does in windows? is there anyway to reinstall usb support or something?

---

### Post by Scythe!? on 2006-12-23
Ive just been reading the bootup log and the port that the mouse is in at boot is not being detected. Anyway to fix?

---

### Post by slimdog360 on 2006-12-23
not that I usually suggest this sort of thing but I believe Ive heard RAV TUX talking about having a razor mouse working, maybe he knows how to get it working? I could be wrong though.

---

### Post by Scythe!? on 2006-12-23
I had it working on Dapper fine and Edgy for a while, the problem has only recently started happening. Possibly a patch created a bug?

---

