---
title: "Black rectangle blocking display on the right."
date: 2014-05-01
forum: General Help
---

### Post by anubeon on 2014-05-01
Greetings All,

I've had this issue for a while now, although it has never been particularly pressing as a typically rely on Compiz for my window management. Frequently, although not always, I find that the Ubuntu login/switch-user screen (unity-greeter/lightdm) is blocked on the right hand side by a large black rectangle. Upon recently upgrading to 'Trusty' I discovered that the large rectangle also appears whenever I'm running the elementaryOS window manager, Gala (see picture below). Curiously Compiz has never been affected by this visual glitch.

Does anybody have a clue how to diagnose this issue? I read of a similar issue in this very forum wherein a respondent remarked that a defunct or zombie process might be the culprit, and suggested reason ~/.xsession-errors. I've checked for both defunct and zombie processes, and read through xsession-errors and I can't identify a culprit at all.

Any help would be greatly appreciated.

Regards,

Lee.

P.S.: I'm running under Ubuntu 'Trusty' 14.04 x86-64, with an NVIDIA GeForce 8400M GT GPU running under the recommended nvidia-331 proprietary driver.

[IMG]https://pbs.twimg.com/media/BmjgF8UCYAAhkBk.png:large[/IMG]

---

### Post by grumblebum2 on 2014-06-02
Try getting info by running
```
xwininfo
```
and clicking on the shaded area.

---

### Post by anubeon on 2014-06-19
Greetings and thank you for responding grumblebum2.

I apologise for not responding sooner myself but for some reason I'm not getting e-mail alerts on this thread. 

This issue appears to have cleared itself up with respect to Gala, but has returned to lightdm/unity greeter. Do you have any idea how I might go about executing xwininfo from within lightdm/unit-greeter? I've tried lighdm --test-mode but even if I could figure out how to execute commands from within lightdm/unity-greeter, the aforementioned black rectangle doesn't appear in test mode.

Regards,

Lee.

---

### Post by anubeon on 2014-09-05
Do you have any idea how I might go about executing xwininfo or similar from within Unity Greeter/LightDM? The issue has cleared up with respect to Gala, but remains persistent and annoying within Unity Greeter.

Oh and also… bump. ;-)

---

