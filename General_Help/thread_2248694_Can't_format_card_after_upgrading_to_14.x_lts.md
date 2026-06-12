---
title: "Can't format card after upgrading to 14.x lts"
date: 2014-10-16
forum: General Help
---

### Post by michael-piziak on 2014-10-16
I use to format my SD hc camera card by right clicking the image of it and choosing format.  After upgrading to 14.x it doesn't give the format option anymore.  Any suggestions on how to format the card while it's mounted in the computer now ?

---

### Post by Dennis N on 2014-10-16
What image are you clicking on?  If you mean the desktop icon, in Lubuntu 14.04, you are right - there is no format option in their right click menu. Prior to Lubuntu 14.04, there were no desktop icons shown for external devices, so you couldn't have done this previously. You can't do it from the file manager using the icon for the  SD card's folder either - no such option.

A way to format your card is to use gparted, unmount the file system on the card, and choose **Partition > Format to**

---

### Post by michael-piziak on 2014-10-16
> **Dennis N said:**
> What image are you clicking on?  If you mean the desktop icon, in Lubuntu 14.04, you are right - there is no format option in their right click menu. Prior to Lubuntu 14.04, there were no desktop icons shown for external devices, so you couldn't have done this previously. You can't do it from the file manager using the icon for the  SD card's folder either - no such option.

A way to format your card is to use gparted, unmount the file system on the card, and choose **Partition > Format to**


In version 12.04 LTS, when the volume icon showed up in the dock on the left, I could right click it's icon and format.  I did it hundreds of times, so I know an icon appeared for a card in the card reader or even a thumb drive - just as they still appear (but no right click format option now with 14.x)

---

### Post by Dennis N on 2014-10-16
You may be thinking of Ubuntu 12.04 and the 'dock' being the Unity Launcher - perhaps it is possible there. There was never a Lubuntu 12.04 LTS version. I also checked a still-installed Lubuntu 12.10, and it can't be done.

---

### Post by michael-piziak on 2014-10-16
> **Dennis N said:**
> You may be thinking of Ubuntu 12.04 and the 'dock' being the Unity Launcher - perhaps it is possible there. There was never a Lubuntu 12.04 LTS version. I also checked a still-installed Lubuntu 12.10, and it can't be done.

Yes, I had Ubuntu 12.04 LTS

---

