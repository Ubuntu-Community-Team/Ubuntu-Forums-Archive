---
title: "Turning off the monitor?"
date: 2008-06-02
forum: General Help
---

### Post by ReeRD on 2008-06-02
How do I make my monitor turn off after certain time of inactivity? It never turns off, only blackens.

I'm on a desktop machine.

---

### Post by bingoUV on 2008-06-02
When it goes off it will blacken, right?

Why do you say it does not go off? Is there slight light issuing from it? Try this in a terminal
```

xset dpms force off

```

Move the mouse to reactivate the monitor. Do you call it going off, or blackening?

---

### Post by ReeRD on 2008-06-03
Blackening is just that - blackening. The screen goes black but the monitor stays turned on.

I want it to turn off completely after certain inactivity time. This functionality is present on Kubuntu, Windows, etc.

---

### Post by cariboo on 2008-06-03
The settings you are looking for are in System-->Preferences-->Screensaver. Click on the Power Management button.

Jim

---

### Post by bingoUV on 2008-06-03
1. When it goes off it will blacken, right? Okay, do this experiment. Turn off the monitor manually. Has it blackened now? How is it different from your blackening but not turned off? Just the LED?

2. Why do you say it does not go off? Is there slight light issuing from it? Turn off all lights in the room. Does some light come out of the monitor except the LED?

3. Did you try the command? 
```

xset dpms force off

```
Does something happen? What do you call this? Blackening or going off?

---

