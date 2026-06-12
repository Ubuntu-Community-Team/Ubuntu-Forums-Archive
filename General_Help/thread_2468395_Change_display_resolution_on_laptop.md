---
title: "Change display resolution on laptop"
date: 2021-10-27
forum: General Help
---

### Post by nickjhs on 2021-10-27
Hi, I had an issue with the display and tried changing the resolution, this ended up with a  blurred and rapidly flickering screen. I couldn't get to the revert button so did a hard reboot. Now the only way to use the laptop is in recovery mode. I cannot find how to change the resolution outside of recovery mode.  Help would be greatly appreciated. Cheers

---

### Post by grahammechanical on 2021-10-27
When we load Ubuntu from the recovery menu it loads with a low resolution open source video driver. This should be sufficient to open System Settings>Screen Display. The resolution can be changed from there. Are you saying that when you change the resolution and reboot the problem of the blurred and rapidly flickering screen has not been solved?

Are you using a proprietary video driver? You could try opening Software & Updates>Additional Drivers and deactivating the proprietary video driver. A reboot should load Ubuntu with an open source video driver but with a better resolution than we get with recovery mode. Then try changing the video mode.

Regards

---

### Post by nickjhs on 2021-10-28
Thanks Graham, yes I am using Nvidia drivers. I tried switching to the nouveau driver but it has a long list of unmet dependencies. I tried installing the dependencies and I am told that the newest version is already installed. Is there a way of deleting the Nouveau driver and reinstalling? Cheers

---

