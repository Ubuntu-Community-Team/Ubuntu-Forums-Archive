---
title: "edgy wont reboot"
date: 2007-02-03
forum: General Help
---

### Post by fakie_flip on 2007-02-03
Not long after I had a new install of Ubuntu 6.10 Edgy using the 32 bit version because the 64 bit version would not install, I tried "sudo reboot". The usplash screen with "Ubuntu" and the logo with the orange in a progress bar shows, but the orange is not there. The progress bar is empty. It stays at that part and never reboots or finishes shutting down, so it can reboot. I tried going to System>Quit>Restart and I see the same usplash screen except this time the progress bar is full of orange. The orange goes all the way down until there is a little left and stays there. My computer stays there, so I have to turn it off from the power button on the power supply. I tried disabling usplash from starting and running using BUM. However usplash is still there and is hiding the Linux boot process. BUM says it is not starting on boot, but it is lying about that. Doing a "sudo poweroff" or shutdown from the gui works, but reboot has never worked.

---

### Post by MoLE on 2007-02-11
First thing I would suggest is to disable usplash so you can see where the 'freeze' occurs.

Instructions taken from [here]("http://www.cs.cornell.edu/~djm/ubuntu/").

   1. (optional) To disable USplash, if, like me, you find it ugly:

      sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
      sudo gedit /boot/grub/menu.lst

      Remove the splash option from the appropriate lines. I.e., Change:

      kernel          /boot/... root=... ro quiet splash

      to:

      kernel          /boot/... root=... ro quiet

---

