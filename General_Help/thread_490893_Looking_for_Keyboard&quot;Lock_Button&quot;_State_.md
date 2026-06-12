---
title: "Looking for Keyboard/&quot;Lock Button&quot; State Notifier"
date: 2007-07-03
forum: General Help
---

### Post by GumbyX on 2007-07-03
I am in search of a keyboard state notifier for ubuntu. I don't know what else to call it. All it does it show some kind of notification on the screen when the "* lock" keys is pressed, telling you if it is on or off. My keyboard is wireless and the receiver has these notification lights on it, but the receiver is under my desk, making it hard to tell what locks are on. I wouldn't be surprised if most people have something like this on their laptops (I know for a fact that IBM installs something like this on thinkpads now) or included in the winXP software to their wireless keyboards (came with the software for my logitech wireless keybaord). I am just looking for a linux alternative, if one exists.

Thanks ahead of time for the info, and if possible (to ask a quick question on top of this), does anyone know of a decent, Adobe Premier-like video editor for linux/ubuntu?

---

### Post by gfixler on 2007-07-03
You could grab gkrellm from Synaptic, and disable everything but the LEDs under the plugins section. It's a tiny floating window that lists real-time states of almost anything in the computer.

---

### Post by GumbyX on 2007-07-03
That does work, but I cannot get rid of the rest of the default plug-ins. Does anyone know how to get shut them off, or of any other programs?

---

### Post by gfixler on 2007-07-05
The other stuff isn't in the plugins - it's all in the Builtins section of the configuration, just above Plugins. I was able to remove all but the 3 little lights for the 3 lock keys, but you have to look around in there to find all the checkboxes.

---

