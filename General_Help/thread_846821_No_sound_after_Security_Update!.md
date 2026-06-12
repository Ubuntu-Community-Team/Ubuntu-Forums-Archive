---
title: "No sound after Security Update!"
date: 2008-07-01
forum: General Help
---

### Post by CesarRB on 2008-07-01
I am not new to Linux, but I am not any superuser. I just like Linux but most of the time I have no idea where to start or what to do when a problem arises. This was the case two days ago when I installed the security updates that piled up, while I was out on a trip. I installed every thing that the system suggested (approx. 250 MB) and after that I have no sound. The speaker icon in the Panel shows the red circle and bar as it was muted. But I have tried to open the Volume Control and I received the next message:

*No volume control GStreamer plugins and/or devices found.*

If I go the Sound Preferences and Test the Sound Events, I received the next message:

*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument*

Any ideas of what could have gone wrong?!

UPDATE! (07/03/2008)

By the way, I am using Hardy in my box. I made a test booting from a Kubuntu 7.04 live CD and had no problems with the sound. Any ideas of where to go from here?


Thanks,
Cesar.

---

### Post by CesarRB on 2008-07-03
SOLUTION

I found that the problem was a conflict with the modem driver. I have a HDA sound card (whatever that means) and I tried to install a HSF Conexant modem driver (I am not even sure if it is a HSF modem). I removed the driver and the sound is back.

Thanks,
Cesar

---

