---
title: "Desktop does not extend to second screen"
date: 2022-10-04
forum: General Help
---

### Post by brad_richards on 2022-10-04
For literally years, I have used Xubuntu with two screens. This morning - no. One screen is blank (black, not even a background) except it does display the mouse pointer.

I can mirror the screens and both screens display the desktop. However, as soon as I set them to be "next to" each other, the secondary screen is simply black. Again, except that it does display the mouse pointer, so the screen is active.

FWIW, this is Xubuntu 22.04, using Nvidia driver version 515 (the drivers tool shows "manually installed" and cannot be changed).

Never seen anything quite like this...suggestions appreciated. Working with only one screen is...painful.

---

### Post by brad_richards on 2022-10-04
Answering my own question: Reinstalling the Nvidia drivers solved the problem:

sudo ubuntu-drivers autoinstall
sudo reboot

---

### Post by MAFoElffen on 2022-10-04
Glad to hear you found your solution. Please use the "Thread Tools" link in the upper right of this page to mark this as 'Solved" so that others can find your solution to their similar issues.

---

