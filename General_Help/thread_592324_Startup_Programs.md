---
title: "Startup Programs"
date: 2007-10-26
forum: General Help
---

### Post by CheeseQueen452 on 2007-10-26
When I go to preferences-->sessions, what programs can I safely remove from startup? I don't use bluetooth, the print applet, tracker, or the evolution notifier. Can those be removed without causing any problems?

---

### Post by CheeseQueen452 on 2007-10-26
Anyone?

---

### Post by chrismine on 2007-10-26
I cannot tell you but wahat I do know is that when I addeda bluetooth dongle  to my PC I struggled for days to get it to work after Irebooted. Then the lights went on and I remembered that I disabled the bluetooth in startup!

Just keep this in mind when something is not working later.

---

### Post by CheeseQueen452 on 2007-10-26
As I said, I don't use bluetooth. Unless someone gives me a good reason to keep it on startup, I don't want it running when I don't even need it.

> **chrismine said:**
> I cannot tell you but wahat I do know is that when I addeda bluetooth dongle  to my PC I struggled for days to get it to work after Irebooted. Then the lights went on and I remembered that I disabled the bluetooth in startup!

Just keep this in mind when something is not working later.

---

### Post by evilc on 2007-10-26
Just un-tick the one you don't want to startup, if you find you made a mistake later on just re-tick.

---

### Post by drs305 on 2007-10-26
Here is a way to check what it does. In System, Preferences, Sessions, select edit and it will tell you what app or applet is being called. In this case it is 'bluetooth-applet'.   Then, in terminal, type
```
man bluetooth-applet
```

Here's what it says in the description:
bluetooth-applet  will  stay  in  your  GNOME panel as a Bluetooth icon and will pop up a dialog whenever a passkey (aka PIN) is required from the Linux Bluetooth stack.  bluetooth-applet is part of bluez-gnome, see also [http://www.bluez.org](http://www.bluez.org)


You may have already read this but newer users may not be aware of this capability. You can also check synaptic for a description of what a program or applet does, but in this case bluetooth-applet is not listed in mine.

---

