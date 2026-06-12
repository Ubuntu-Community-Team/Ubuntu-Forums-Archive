---
title: "Ubuntu will not install (black screen)"
date: 2018-01-07
forum: General Help
---

### Post by nyves on 2018-01-07
I burned it correctly to a dvdr restarted and tried to install twice and it just stays on a black screen for a very long time

---

### Post by mastablasta on 2018-01-08
what kind of setup? Secure boot on or off? BIOS or UEFI?
What hardware are you using? can you boot into a live session?

Did you check the md5sum of the downloaded image?

---

### Post by MoebusNet on 2018-01-08
Many times this can be caused by a video card that is not currently supported by the installation media. A very new or very old video card model would be an example of this. Many times you can get to a visible screen by using boot parameters: [https://help.ubuntu.com/community/BootOptions?action=show&redirect=BootParameters](https://help.ubuntu.com/community/BootOptions?action=show&redirect=BootParameters) Using the VESA driver may make your screen visible with a basic display so that you can attempt to find the correct video card driver, if that indeed is the issue. Other assistance can be found here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

