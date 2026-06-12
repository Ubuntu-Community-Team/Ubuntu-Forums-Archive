---
title: "Laptop goes blank on suspend"
date: 2022-06-03
forum: General Help
---

### Post by triplemaya on 2022-06-03
My laptop usually suspends as per setting when I close the lid. But every so often it does not. On reopening, screen is blank and no response to keyboard or touchpad, and if I type in the shut down command nothing happens. So a hard restart required. How do I go about finding what is happening and how to fix it. Thanks. 
Running Ubuntu mate 1.240
Laptop is HP Elitebook 850 i7 with AMD Radeon™ HD 8730M

---

### Post by #&amp;thj^% on 2022-06-03
A little more help is needed from you:
```
inxi -G
```
And since your using the X11 session, you can try a different method of suspending IE:
```
systemctl suspend
```
This will rule out screen blanking, screen locking etc.
Try that and let us know.

---

### Post by kurt18947 on 2022-06-05
> **1fallen said:**
> A little more help is needed from you:
```
inxi -G
```
And since your using the X11 session, you can try a different method of suspending IE:
```
systemctl suspend
```
This will rule out screen blanking, screen locking etc.
Try that and let us know.

And if you create a keyboard shortcut, the above command is a one key stroke affair:

Settings -- Keyboard Shortcuts -- scroll to the bottom of the window and you should see a + sign. Click that and you can assign a command to a key or combination of keys. My desktop machine I used the "pause" key. Give it a name, in Command I have
```
systemctl -i suspend
```
Then for Shortcut  Click on Set Shortcut then press the desired key or combination you wish to assign the shortcut to.
Now it's one key press to suspend the machine.

---

### Post by Impavidus on 2022-06-05
> **triplemaya said:**
> So a hard restart required.
Hard restarts are something to be avoided. Have you tried these workarounds too?

- In the past there have been some similar bugs. It worked to switch to some tty, then back to the GUI, using ctrl+alt+F1 followed by ctrl+alt+F7. The switch back the the GUI must be one particular F-key, but it's not the same on every Ubuntu system, so best to try this first when your computer works fine. Switching to the tty works with just any other F-key, at least up to F6.

- Have you tried the magic SysRq key to reboot? That's cleaner than pressing the power button. It's not fully enabled by default, so you may have to tweak it.

---

