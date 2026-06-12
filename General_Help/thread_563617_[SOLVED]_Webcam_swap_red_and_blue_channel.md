---
title: "[SOLVED] Webcam swap red and blue channel"
date: 2007-09-30
forum: General Help
---

### Post by peabody on 2007-09-30
[B]I have solved the problem, I put the following line in my /etc/modprobe.d/options file:

options gspca force_rgb=1

Worked like a charm on reboot.  Colors are wrong in camorama now, but they're correct in youtube's quick capture which is what I needed.
[/B]

I have an intel easy pc camera (old sucker, usb 1) which works perfectly with the camorama software as shown in the attached shot.

I'll admit it isn't a very good shot, but the color is correct, my skin tone is correct.  Contrast that to a youtube video I made using the cam here:

[http://www.youtube.com/watch?v=cAPZHZXOXXY](http://www.youtube.com/watch?v=cAPZHZXOXXY)

Nothing but a blue tinge, which is characteristic of a common problem involving byte order and rgb where the red and blue channels get swapped.

My question is, is there a way (some v4l setting?) where I can fix this so the flash app on youtube gets the correct colors?  Camorama is apparently doing something to tell the v4l drivers that the byte order should be swapped for correct colors.  Is there a way I can turn that on myself?

---

