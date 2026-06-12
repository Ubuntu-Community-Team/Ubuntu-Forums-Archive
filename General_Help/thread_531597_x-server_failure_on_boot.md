---
title: "x-server failure on boot"
date: 2007-08-21
forum: General Help
---

### Post by cetol on 2007-08-21
Well once again I have proven that I know just enough about  ubuntu to take a working system and trash it, with one hand behind my back even!

Now to the problem... I was trying to compile and install audacity on my system and "make install" didn't install. So after becomming frustrated, as is often the case with me and linux, I stopped working and put the computer up for the night. Lo and behold when I came back to it the next day the #@$%$% x server wouldn't come up.

The error message said it couldn't find module nvidia. I didn't move it!

If left to my own devices I will end up punting (reinstalling). Any suggestions?

---

### Post by tzulberti on 2007-08-21
Maybe you updated you kernel, and do not updated you nvidia driver...

Nevertheless, if you are at the console you could use:
"sudo dpkg-reconfigure xserver-xorg"

Choose nv as the video driver... Then try:
sudo /etc/init.d/gdm restart (user kdm instead of gdm if using kubuntu).

If that fixes the problem try to reinstall de nivida-glx driver.

---

### Post by cetol on 2007-08-22
I did try to reconfigure and selected nv but this did not help. To the best of my knowledge I did not do anything to the kernel.

---

