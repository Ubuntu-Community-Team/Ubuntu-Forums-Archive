---
title: "Undetected Screen Resolution and Monitor Out of Range"
date: 2017-05-10
forum: General Help
---

### Post by petmol on 2017-05-10
Hello,
I'm not particularly a new linux user as i have used linux mint in the past but I've been using windows for the past 2 months. In that mean time I upgraded some hardware namely my GPU to a AMD Radeon HD 6950 which from what I've read the drivers in linux already come preinstalled on the kernel. My big problem comes here my monitor which isn't very new only has VGA input and the GPU doesn't have any VGA output so i bought an adapter which gave me some problems on windows as well due to the fact that neither windows not linux can see the hardware info of the monitor and therefore show me the compatible resolutions. On windows the AMD Catalyst control panel had the fix but for Ubuntu, which i have installed today, the problem is a little harder. The thing is that i have tried using xrandr but when I created the new mode for the resolution of my monitor, 1920x1080@60Hz, and enable it the monitor shows an Out of Range message. I don't know what the problem is so I'm here looking for some help. Thanks in advance.

---

### Post by Autodave on 2017-05-10
A VGA monitor has to report its presence to the video card. This is done through one wire in the cable. If your cable is bad or the adapter doesn't connect properly, the card has no idea what resolution to run. You may be in need of a new monitor. I would try to borrow one with DVI just to see.

---

