---
title: "black screen?"
date: 2007-10-01
forum: General Help
---

### Post by asavage890 on 2007-10-01
hi just installed ubuntu:) whole new world and im lost:confused:...went into restricted drivers(i think)and enabled ati driver, upon requested reboot after initial loading bar-:( black screen:(.....what can i do to reverse or rectify this....many thanks

---

### Post by strabes on 2007-10-01
When it gives you the black screen, hit CTRL+ALT+F1, then enter this command:```
sudo dpkg-reconfigure xserver-xorg
```

Then to reboot your system run:[code]sudo reboot]

Once you get back into a GUI you can follow the instructions located [here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b) to install the proprietary fglrx driver.

You can actually just copy down the commands from the page I linked to and run them after you hit CTRL+ALT+F1 initially. It will do the same thing.

---

