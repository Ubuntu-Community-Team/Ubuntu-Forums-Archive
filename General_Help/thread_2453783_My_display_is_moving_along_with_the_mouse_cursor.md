---
title: "My display is moving along with the mouse cursor"
date: 2020-11-17
forum: General Help
---

### Post by themeditationcenter on 2020-11-17
Hi,
All of a sudden today morning I see my screen is moving along with my cursor. As if the desktop is bigger than the monitor.
I have an additional display monitor and the screen resolution is set to 1920x1080.
The driver I am using is the nvidia proprietary driver which is tested by Ubuntu.
I tried to use the X.Org X driver before but it did not support multiple monitors so was forced to use NVidea.

Not sure how to describe my issue, so I am attaching the video [here]("https://youtu.be/fAmQLHR6YEs").

I am not sure what log files to give. Let me know and I'll attach it here.

Any help on this will be really appreciated.

Regards,
tmc

---

### Post by themeditationcenter on 2020-11-17
I played around and then fixed it by doing this:
Went to System Settings -> Compositor and unchecked "Enable compositor on startup" and rebooted the machine.
This seem to fix it, not sure doing this what other issues are going to come up...but hey it worked for now.

Putting it here in case someone else is facing this issue.

---

