---
title: "Middle mouse button (scroll wheel) event?"
date: 2017-11-17
forum: General Help
---

### Post by Macamba on 2017-11-17
The other day I performed a (manual) update of my Ubuntu system (16.04 LTS). Today I noticed my middle mouse button click is not happening. I have a Logitech blue tooth keyboard and mouse combo. 

I installed > Xautomation and > Xbindkeys, and tried to figure out with > xev what button number the middle button would have. When I scroll the wheel  in the 'Event tester' window I get a lot of events, but licking with the middle button does not generate an event. Has the button mouse handling changed? I do miss my double click! What can I do to get back the middle mouse button click event back? 

FWIW: [Mouse customizatons page]("https://help.ubuntu.com/community/MouseCustomizations")
Install Xautomation and Xbindkeys:```

sudo apt-get install xautomation
sudo apt-get install xbindkeys
```

---

### Post by Macamba on 2017-11-18
After first closing the [wrong thread]("https://ubuntuforums.org/showthread.php?t=2377838") you can close this one too. First because I do not get response, except for closing and moving my thread. Secondly, clicking with the scroll wheel works again, so my problem is moot.

---

### Post by Impavidus on 2017-11-18
I wouldn't be surprised if this turned out to be a hardware error. That's often the case with sudden intermittent mouse problems. The switches inside the mouse may be a bit worn. Or, as this is a wireless mouse, the battery may be poor (and intermittent as the battery performs better as it gets warmer).

---

