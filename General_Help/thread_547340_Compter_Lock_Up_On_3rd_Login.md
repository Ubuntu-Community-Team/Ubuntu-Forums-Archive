---
title: "Compter Lock Up On 3rd Login"
date: 2007-09-09
forum: General Help
---

### Post by measekite on 2007-09-09
The following is what I did and what happened.

Power On Boot

At Login Screen I entered Username and PSW
Login Successful

Log Off
At Login Screen I entered Username and PSW
Login Successful

At Login Screen I entered Username and PSW
Computer Froze.

Cound not even do a Ctrl Alt Backspace.

This happens even if I change users a couple of times.  On the 3rd attempt at logging on the computer locks up.  This does not happen when I switch users, only when I completely log off and then log on again for the 3rd time.

Has anybody experienced this and found a solution.

---

### Post by measekite on 2007-09-10
> **measekite said:**
> The following is what I did and what happened.

Power On Boot

At Login Screen I entered Username and PSW
Login Successful

Log Off
At Login Screen I entered Username and PSW
Login Successful

At Login Screen I entered Username and PSW
Computer Froze.

Cound not even do a Ctrl Alt Backspace.

This happens even if I change users a couple of times.  On the 3rd attempt at logging on the computer locks up.  This does not happen when I switch users, only when I completely log off and then log on again for the 3rd time.

Has anybody experienced this and found a solution.

[COLOR=Red]**SOLUTION**[/COLOR]

The problem kept repeating because since the machine went totalally dead I was forced to do a power off.  When I brought back power and the machine booted up it must have read some dirty information that was saved.  Therefore freezing again on the 3rd logon.

To correct the situation I did a cold start and logged on.  Then I hit the red button and  let Ubuntu do a shut down.  After Ubuntu turned the machine off I could then reboot.  I logged on and off 5 times just to make sure every thing was OK.

If any body in the community has any more information on what went on I would like to hear it.

---

