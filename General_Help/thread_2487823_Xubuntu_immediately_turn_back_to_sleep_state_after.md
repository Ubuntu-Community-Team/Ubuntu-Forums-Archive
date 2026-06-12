---
title: "Xubuntu immediately turn back to sleep state after wake up from suspend"
date: 2023-06-16
forum: General Help
---

### Post by ridwanpratama on 2023-06-16
I'm using xubuntu 23.04

If I suspend my system and go to sleep state, I need to press button multiple time to wake up completely. It just went like this:
suspend -> wake for 1s -> immediately back to sleep -> wake again for 1s (if I press another button on my keyboard) -> back to sleep again -> and keep repeated until it stopped from going back to sleep.

Usually I need to press my keyboard 3-4 times before xubuntu wake up.

This is the result from `journalctl | grep systemd-sleep`:
```

Jun 14 22:40:09 Swift-X systemd-sleep[38733]: Entering sleep state 'suspend'...
Jun 14 22:40:15 Swift-X systemd-sleep[38733]: System returned from sleep state.
Jun 14 22:41:19 Swift-X systemd-sleep[40060]: Entering sleep state 'suspend'...
Jun 14 22:41:22 Swift-X systemd-sleep[40060]: System returned from sleep state.
```



You can see that it just going back to sleep state. I don't have any idea what's happening here.

---

### Post by deadflowr on 2023-06-17
*Thread moved to **General Help***
23.04 is no longer under development and has been released.

---

