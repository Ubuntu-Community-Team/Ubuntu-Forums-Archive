---
title: "Is there a way to start live CD with with command line only?"
date: 2007-06-10
forum: General Help
---

### Post by taphos on 2007-06-10
I have a very old machine which have 128 mb of ram.
This machine had windows millenium installed, but it died.
I want to use ubuntu live to copy some files from windows partition.
When live session is starting it gets to the point where I can see the gnome splash and the start sound is played. But it never goes further, it keeps showing the splash screen for hours. Probably it is because there is not enough memory for the live session.

Can i tell somehow the Ubuntu live CD bootloader not to start xserver?

---

### Post by coffeecat on 2007-06-10
You're right. You haven't got enough memory to run the gnome desktop. Both gnome and kde are quite memory hungry.

One alternative is to use the [Xubuntu]("http://www.xubuntu.org/") live CD. Xubuntu uses the Xfce desktop which is much lighter than gnome. According to the minimum system requirements:

> To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install.So it should be able to do what you want.

---

