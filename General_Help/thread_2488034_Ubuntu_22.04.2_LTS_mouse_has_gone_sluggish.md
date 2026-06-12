---
title: "Ubuntu 22.04.2 LTS mouse has gone sluggish"
date: 2023-06-21
forum: General Help
---

### Post by smeg2 on 2023-06-21
Starting today my laser mouse has gone sluggish, I have tried it on another PC where it works fine so it is not the mouse, it is Ubuntu that is the problem, I have all the latest updates installed, I am using Ubuntu 22.04.2 LTS.

---

### Post by slickymaster on 2023-06-21
*Thread moved to **General Help**.*

---

### Post by smeg2 on 2023-06-23
The mouse is getting worse.

---

### Post by smeg2 on 2023-06-24
It is getting even worse, nearly unusable.

---

### Post by smeg2 on 2023-06-27
Lost the mouse completely today, had to force shutdown with the power button and restart to get it back.

---

### Post by smeg2 on 2023-06-29
Still dodgy as hell, freezing up all the time.

---

### Post by scpatl4now on 2023-07-01
I have also noticed this problem.  It would be nice to get some sort of answer

---

### Post by smeg2 on 2023-07-01
Thanks for the reply, the only one so far.
My mouse is freezing up again.

---

### Post by smeg2 on 2023-07-04
Still playing up, why hasn't this been fixed?

---

### Post by smeg2 on 2023-07-11
With the last update the mouse has improved a little but still lagging behind.

---

### Post by smeg2 on 2023-07-17
Mouse is still playing up.

---

### Post by gezzer2 on 2023-07-18
> **smeg2 said:**
> Mouse is still playing up.

it would help if you could provide some details, mouse type and make, wifi, bluetooth, cable 
have you changed batteries or tried another mouse or anything else you have tried but some more information would help ...

---

### Post by smeg2 on 2023-07-18
Can't remember the mouse make or model, it is a corded mouse, have tried it on another PC and it works fine.

---

### Post by gezzer2 on 2023-07-19
> **smeg2 said:**
> Can't remember the mouse make or model, it is a corded mouse, have tried it on another PC and it works fine.

have you tried increasing mouse speed via settings mouse and touch pad also check that touchpad is disabled (via gnome tweaks) check accessibility settings and if all else fails try another mouse to see if the problem persists ...

---

### Post by smeg2 on 2023-07-19
> **gezzer2 said:**
> have you tried increasing mouse speed via settings mouse and touch pad also check that touchpad is disabled (via gnome tweaks) check accessibility settings and if all else fails try another mouse to see if the problem persists ...

Speed settings are fine, touch pad is disabled, accessibility setting do nothing, the mouse works fine on another PC, can't afford to buy another mouse.

---

### Post by gezzer2 on 2023-07-19
> **smeg2 said:**
> Speed settings are fine, touch pad is disabled, accessibility setting do nothing, the mouse works fine on another PC, can't afford to buy another mouse.

does the mouse have a track ball underneath (the old type did) it if so this may need cleaning have you also tried another USB port and i'm running out of ideas ...

---

### Post by smeg2 on 2023-07-19
> **gezzer2 said:**
> does the mouse have a track ball underneath (the old type did) it if so this may need cleaning have you also tried another USB port and i'm running out of ideas ...

As stated earlier it is a laser mouse, I have tried it in a different USB port it is just the same.

---

### Post by gezzer2 on 2023-07-19
can you loan another mouse from elsewhere to see if that works and eliminate the software ...

---

### Post by smeg2 on 2023-07-19
> **gezzer2 said:**
> can you loan another mouse from elsewhere to see if that works and eliminate the software ...

No I cannot.

---

### Post by #&amp;thj^% on 2023-07-19
I know the mouse gets a bit stuttered if the CPU gets close to max.
have a look at:
```
journalctl -b -e | grep Consumed
```
It might show something.
Effort to help....BTW This a known bug or complaint on wayland, is it the same on X11?

---

### Post by smeg2 on 2023-07-20
> **1fallen said:**
> I know the mouse gets a bit stuttered if the CPU gets close to max.
have a look at:
```
journalctl -b -e | grep Consumed
```
It might show something.
Effort to help....BTW This a known bug or complaint on wayland, is it the same on X11?

I have no idea how to use that code.
The mouse plays up nearly all the time, I don't think it has anything to do with CPU usage.

---

### Post by #&amp;thj^% on 2023-07-20
> **smeg2 said:**
> I have no idea how to use that code.
The mouse plays up nearly all the time, I don't think it has anything to do with CPU usage.

Well we don't have a lot info coming from you to hunt the problem down.
You use the code to see what is the top CPU culprit ie:
```
journalctl -b -e | grep Consumed
Jul 20 10:40:48 me-Lenovo-Legion-5-15ARH05 systemd[4044]: tumblerd.service: Consumed 41.547s CPU time.
Jul 20 11:11:07 me-Lenovo-Legion-5-15ARH05 systemd[4044]: tumblerd.service: Consumed 1.787s CPU time.
Jul 20 12:26:05 me-Lenovo-Legion-5-15ARH05 systemd[4044]: app-flatpak-com.sublimetext.three-28933.scope: Consumed 18.097s CPU time.
Jul 20 12:31:18 me-Lenovo-Legion-5-15ARH05 systemd[4044]: tumblerd.service: Consumed 1.071s CPU time.

```
And again have not heard back if it's the same behavior on a X11 session.
I'm not after thoughts here just facts.

---

### Post by smeg2 on 2023-07-20
> **1fallen said:**
> Well we don't have a lot info coming from you to hunt the problem down.
You use the code to see what is the top CPU culprit ie:
```
journalctl -b -e | grep Consumed
Jul 20 10:40:48 me-Lenovo-Legion-5-15ARH05 systemd[4044]: tumblerd.service: Consumed 41.547s CPU time.
Jul 20 11:11:07 me-Lenovo-Legion-5-15ARH05 systemd[4044]: tumblerd.service: Consumed 1.787s CPU time.
Jul 20 12:26:05 me-Lenovo-Legion-5-15ARH05 systemd[4044]: app-flatpak-com.sublimetext.three-28933.scope: Consumed 18.097s CPU time.
Jul 20 12:31:18 me-Lenovo-Legion-5-15ARH05 systemd[4044]: tumblerd.service: Consumed 1.071s CPU time.

```
And again have not heard back if it's the same behavior on a X11 session.
I'm not after thoughts here just facts.

Again, I have no idea how to use the code.
I also have no idea what an X11 session is.

---

### Post by #&amp;thj^% on 2023-07-20
> **smeg2 said:**
> Again, I have no idea how to use the code.
I also have no idea what an X11 session is.
Fair enough maybe someone else will be better suited to help you then. ;)
```
inxi -G | grep x11
  **[COLOR="#FF0000"]Display: x11 server[/COLOR]**: X.Org v: 1.21.1.7 driver: X: loaded: nvidia

```

---

### Post by smeg2 on 2023-07-25
Since the last update the mouse seems to have been fixed.

---

