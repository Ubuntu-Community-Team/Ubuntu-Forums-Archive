---
title: "Unable to turn on visual effects"
date: 2008-05-10
forum: General Help
---

### Post by JohnJSal on 2008-05-10
Hi everyone. When I go to System > Preferences > Appearance > Visual Effects and choose either Normal or Extra, I get a message saying Ubuntu can't enable visual effects. What would cause this? My graphics card and processor are at least decent enough to do Normal, if not Extra.

Thanks.

---

### Post by FuturePilot on 2008-05-10
What is the output of
```
compiz --replace
```
and what graphics card do you have? Did you install any drivers available from System&#8594;Administration&#8594;Hardware Drivers?

---

### Post by JohnJSal on 2008-05-10
> **FuturePilot said:**
> What is the output of
```
compiz --replace
```
and what graphics card do you have? Did you install any drivers available from System&#8594;Administration&#8594;Hardware Drivers?

No, I didn't use the drivers utility. It does, however, show my card there with the status "not in use" and an empty checkbox under "Enabled". Should I enable it?

---

### Post by FuturePilot on 2008-05-10
> **JohnJSal said:**
> No, I didn't use the drivers utility. It does, however, show my card there with the status "not in use" and an empty checkbox under "Enabled". Should I enable it?

Yes. You need that driver for Compiz.

---

