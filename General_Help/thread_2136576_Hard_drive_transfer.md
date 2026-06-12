---
title: "Hard drive transfer"
date: 2013-04-18
forum: General Help
---

### Post by nerdtron on 2013-04-18
So my motherboard had a busted capacitor and doesn't boot anymore. I tried transferring the hard drive to another computer to continue my work. This one seems simple enough as I have tried it before and it just works.

But now, I remembered that I had installed Nvidia Drivers on the old computer, and now every time I boot into the new computer, it boots into a command line. I logged in and tried to startx but it failed. Now I'm stuck. can you help me? Even a fail safe low graphics mode will do. I just need a GUI to work on.

Thanks!

---

### Post by dargaud on 2013-04-18
Run nvidia-xconfig as root, it should reset your graphical config. Or possibly re-run the ./NVIDIA... installer.

---

### Post by nerdtron on 2013-04-18
Ok will try this, but new motherboard isn't nvidia. Is there a way to uninstall the nvidia drivers through the command line and leave just the default ubuntu drivers?

---

### Post by dargaud on 2013-04-18
Hah, OK, I understood the reverse. Run 'sudo ./NVIDIA... --uninstall' and see what happens. And/or 'sudo aptitude remove nvidia-current' and check what's left with 'sudo aptitude search nvidia'

---

### Post by nerdtron on 2013-04-18
I have removed nvidia drivers by using sudo apt-get remove --purge nvidia-current
Still no progress.

---

