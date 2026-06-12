---
title: "AMD GPU crashing when playing game"
date: 2019-06-07
forum: General Help
---

### Post by andreashhhansen on 2019-06-07
Hello, I have had a problem for about the last week on my Ubuntu 18.04  machine. I recently upgraded my GPU to a RX 580, but now it seems to  crash every time I've played a game for a bit. This time interval isn't constant, it can vary from after a few minutes up to an hour. When the crash happens,  the screen freezes, but the rest of the system is still running. I can still do stuff like  REISUB and SSH into the machine. Things I've tried so far include  reinstalling the mesa-vulkan-driver and ubuntu-desktop, but this didn't  help with the issue. Can anyone recommend any solutions?
Thank you for any answers!

---

### Post by Autodave on 2019-06-07
Some info on your machine please.  What GPU were you using previously?

---

### Post by andreashhhansen on 2019-06-07
Right, I previously used a Nvidia GTX 960. Other than that my kernel version is 4.15.0-51-generic and my graphics driver is X.Org Radeon RX 580 Series (POLARIS10, DRM 3.23.0, 4.15.0-51-generic, LLVM 7.0.0) Version 4.4 (Compatibility Profile) Mesa 18.2.8

---

### Post by corradoventu on 2019-06-08
did you check the temperature?

---

### Post by andreashhhansen on 2019-06-08
I just ran a stress (glmark2) test for about 30 minutes, and the temperature stabilized from 66-75 degrees

---

### Post by Autodave on 2019-06-08
Did you remove the Nvidia driver?

---

### Post by andreashhhansen on 2019-06-08
No, I had not. I have now done so, and will report back if the problem persists. Thank you very much!

---

### Post by andreashhhansen on 2019-06-08
I removed all nvidia drivers, but this unfortunately didn't solve the problem

---

### Post by andreashhhansen on 2019-06-08
I have tested some games throughout the day, and here is the ones I have found to be crashing: Hearts Of Iron IV, Starcraft (Running on WINE), XCOM 2, Dirt Rally and Project Cars 2 (Running on Proton). I have also not been able to make Minecraft or Rimworld crash. I don't know if this will help, but here you go.

---

