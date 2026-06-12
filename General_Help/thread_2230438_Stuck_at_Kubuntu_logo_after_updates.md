---
title: "Stuck at Kubuntu logo after updates"
date: 2014-06-19
forum: General Help
---

### Post by laughton.andrew on 2014-06-19
I have just done a daily update to the latest version of Kubuntu, and now my computer gets stuck booting.
I get the "Kubuntu" and logo glowing and fading in the middle, but will not go any further.

I have it going in recovery console mode, then startx works as a smaller font console, and I then managed to get firefox running to type this.
I am running a Dell Inspiron 15R notebook.

Is anybody else having similar problems ?

---

### Post by Bucky Ball on 2014-06-19
*Thread moved to **General Help**.*

Welcome. Please do not hijack other user's threads. Just post one of your own with a descriptive title in the appropriate forum and with as much relevant info as you can think of. You'll greatly improve your chances of getting help. Thanks. 

Was the machine working fine before the updates? Which release? Is this a fresh install?

---

### Post by xc3RnbFO8P on 2014-06-19
You can try to rename .kde to .kde back (hidden folder in your home folder) and restart again

---

### Post by hamishmb on 2014-06-19
If you get to the grub menu, press "e" over the highest non-recovery boot option, and add "text", and remove "quiet" and "splash" from the line starting with linux, do you see any errors?

Thanks,
Hamish

---

