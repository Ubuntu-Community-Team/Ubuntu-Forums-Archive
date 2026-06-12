---
title: "Can't boot into ubuntu 7.10"
date: 2007-12-01
forum: General Help
---

### Post by lszanto on 2007-12-01
Today for my birthday I recieved a laptop so went and straight away installed ubuntu 7.10 to dual boot with vista. Everything went fine and grub worked properly and booted into ubuntu fine but after doing a few tasks it seemed to freeze up so I turned the computer off without shutting down properly which was a dumb thing to do and now for some reason when I choose ubuntu from the grub boot menu it just gives me a black screen and doesn't boot in to ubuntu. So does anybody know how to fix this or what i've done wrong?

thanks in advance, Luke

---

### Post by lszanto on 2007-12-01
Please help? :(

---

### Post by Craigus on 2007-12-01
While it isn't a particularly scientific, problem-solving approach, you could just try reinstalling. Is there stuff on the ubuntu partition that you need to keep ?

---

### Post by lszanto on 2007-12-01
Nah I think i'll just go for a reinstall.

---

### Post by lszanto on 2007-12-01
I've reinstalled now and I have the same error restarting normally, all I have done is installed ubuntu, the restricted drivers for my ati card, xserver-xgl and the compiz manager and when I attempt to boot into ubuntu it just gives me a blank black screen which will just sit there until I turn it off, please help as this is getting annoying i have installed it 3 times so far today.

---

### Post by PmDematagoda on 2007-12-01
Go to Recovery Mode and do:-
```

dpkg-reconfigure xserver-xorg
```

Select the driver as vesa, after reconfiguration is done do:-

```
startx
```

To see if you can get the GUI to work.

---

### Post by lszanto on 2007-12-01
I have done the above and it seemed to get the GUI to work and the computer will start and boot into ubuntu but some of the graphics are distorted and compiz doesn't work either, any other tips?

---

### Post by PmDematagoda on 2007-12-02
Well, I did give you that command on the basis that you could get the GUI back again even though it won't be as flashy as before.

But if it does not fit you, then remove the drivers and reinstall them again using the Restricted Drivers Manager, that could fix your problem.

---

