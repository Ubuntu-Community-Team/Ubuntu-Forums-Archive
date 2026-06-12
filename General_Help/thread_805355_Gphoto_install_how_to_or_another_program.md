---
title: "Gphoto install how to or another program?"
date: 2008-05-23
forum: General Help
---

### Post by creekchub on 2008-05-23
i have a kodak digital camera that i would like to download pic via usb.  when i plug into the usb port it is not even recognized.  i've been looking around and came up with a program Gphoto and my camera is listed. anyhow i downloaded and it is on my desktop screen now how do i go about installing it so i can view and upload pics. or is there a better alternative program?

---

### Post by creekchub on 2008-05-25
come on now i've done some searching and have not found an answer.  i did try a poloroid digital camera in the usb and ubuntu recognized it.  someone has to have a answer for me.

---

### Post by DemonSpeedster on 2008-09-19
> **creekchub said:**
> come on now i've done some searching and have not found an answer.  i did try a poloroid digital camera in the usb and ubuntu recognized it.  someone has to have a answer for me.

You can always use a card reader for your camera's memory card if your camera can not be recognized as sb storage device

---

### Post by Maddog Battie on 2009-05-08
I know this is an old thread but an answer (I believe) is as follows:

bring up a terminal and type the following:
[FONT="Courier New"]
sudo apt-get install gphoto2[/FONT]

This should do the download and install for you.

You can then try things such as the following:

[FONT="Courier New"]gphoto2 --auto-detect[/FONT]

[FONT="Courier New"]gphoto2 --summary[/FONT]

Hopefully that is useful to somebody.

---

