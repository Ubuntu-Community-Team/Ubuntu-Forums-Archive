---
title: "Mouse Issue (Mouse 6, 7) MX500"
date: 2007-04-27
forum: General Help
---

### Post by AlexDe on 2007-04-27
I've looked for a couple hours now and it's driving me nuts, so I've decided to try my last resort..

Some reason 'xev' is showing my mouse 6,7 (side keys) to be bound to 'Button2' and 'Button3'.. I cannot for the life of me figure out why / how to fix them accordingly.

I'm not currently running anything to bind, just default Ubuntu (Feisty) configuration... below is my mouse section of xorg.conf, if you need anything else please let me know.

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "7"
EndSection

```

Thanks!

---

### Post by Lapino on 2007-04-28
I had this problem too, and changing the protocol to ExplorerPS/2 helped. Don't know if this will work for everyone, but give it a try.

---

### Post by Angry penguin on 2007-04-28
[http://ubuntuforums.org/showthread.php?t=65471&highlight=mx500](http://ubuntuforums.org/showthread.php?t=65471&highlight=mx500)

---

### Post by AlexDe on 2007-04-28
> **Lapino said:**
> I had this problem too, and changing the protocol to ExplorerPS/2 helped. Don't know if this will work for everyone, but give it a try.

Worked perfectly, thanks!

> **Angry penguin said:**
> [http://ubuntuforums.org/showthread.php?t=65471&highlight=mx500](http://ubuntuforums.org/showthread.php?t=65471&highlight=mx500)

Might want to read the post before replying ;)

---

### Post by Angry penguin on 2007-04-28
You asked a question about configuring an mx500, i linked to a thread on configuring the mx500. Your snide comment was completely unnecessary.

---

