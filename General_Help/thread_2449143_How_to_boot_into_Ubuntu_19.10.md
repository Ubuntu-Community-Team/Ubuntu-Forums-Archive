---
title: "How to boot into Ubuntu 19.10"
date: 2020-08-20
forum: General Help
---

### Post by Graham_White on 2020-08-20
I am currently running Ubuntu 20.04, and have no problems with it, except that I have software (namely Turboprint) which will only run under Ubuntu 19.10 and older. So, my problem is: how do I boot into
Ubuntu 19.10? Have tried booting with escape key pressed, pressing escape key during boot process, and so on. Always end up in Ubuntu 20.04. What am I doing wrong? 
Thanks

---

### Post by crip720 on 2020-08-20
19.10 is gone if you upgraded.  Will need to install 19.10 as a dual boot or VM.  Could also try this for turboprint to see if you can make it work on 20.04.  [https://www.turboprint.info/support/viewtopic.php?t=7145](https://www.turboprint.info/support/viewtopic.php?t=7145)

---

### Post by grahammechanical on 2020-08-20
The key to press to bring up the Grub boot menu is Shift not Escape.

If there is only one installation of Linux on the machine then we will not see a boot menu. If you are dual booting between Ubuntu 19.10 and 20.04 then the Grub boot menu should appear automatically.

If you are sure that you have an install of Ubuntu 19.10 on that machine then you could try running this command in the terminal of 20.04.

```
sudo update-grub
```

The Grub configuration file will be re-written to include all installations of Linux that can be found.

Regards.

---

