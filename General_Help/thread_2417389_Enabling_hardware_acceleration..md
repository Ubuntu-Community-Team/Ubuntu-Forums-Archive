---
title: "Enabling hardware acceleration."
date: 2019-04-23
forum: General Help
---

### Post by rocco.martinello on 2019-04-23
Hi to all!
I'm having issues watching videos on YouTube with Firefox.
I think the problem is related to hardware acceleration: how can I enable it of Firefox?
I heard that to do this it is necessary edit the .profile  file in the home directory and add the line export MOZ_ACCELERATED=1 MOZ_WEBRENDER=1.
Is it correct?
And how can I do this modification?
P.S.: I can't install Nvidia drivers because doing this cause Ubuntu freezing on boot. However I think enabling hardware acceleration will fix all problems.

---

### Post by SeijiSensei on 2019-04-23
```
However I think enabling hardware acceleration will fix all problems. 
```

Not without the NVIDIA driver installed I suspect.  Hardware acceleration offloads the decoding of H.264 content to the card's video hardware. You need to have the driver installed to enable communication between an application and the video hardware.

What NVIDIA card do you have?  How did you install the driver? The only reliable way is to use the "Driver Manager" in System Settings. Don't try to install a driver from any other location.  If the driver is installed correctly, you shouldn't have crashing at boot.

---

