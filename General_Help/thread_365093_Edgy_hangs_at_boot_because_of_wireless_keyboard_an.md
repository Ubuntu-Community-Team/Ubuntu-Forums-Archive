---
title: "Edgy hangs at boot because of wireless keyboard and mose"
date: 2007-02-19
forum: General Help
---

### Post by imihai on 2007-02-19
hi all,
some weeks ago i have bought a TRUST wireless kit: keyboard and mouse! It works great! But since then, every time I start the PC, right after GRUB, it hangs at the Ubuntu start progress bar and it won't go from there! I have to hit the reset button, the PC restarts and everything is fine! If I unplugg the kit from the USB port and start the PC , no problem! I think I must add something somewhere! But what and where?

---

### Post by kerry_s on 2007-02-19
Try going in to your bios and turn on usb legacy options for keyboard and mouse.

---

### Post by imihai on 2007-02-19
i think I wasn't clear enough! The kit works while bios and then grub initiate! at least the keyboard does! The start process hangs at the Ubuntu progress bar! my problem is that I have to hit th e RESET button and then everything is ok! It goes beyond the Ubuntu start progress bar !

---

### Post by kerry_s on 2007-02-19
Change the boot so you can see, at start press e than move to the second line and press e again take out the last two words "quiet splash" then press enter and b. Now you should be able to see where it gets stuck, my guess will be on the usb, since you don't want to turn on legacy mode which corrects the problem of wireless not responding to probes because its wireless and only activates during use. Done with you.

---

