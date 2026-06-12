---
title: "upgraded video card, need to re-discover"
date: 2007-01-04
forum: General Help
---

### Post by oldmanstan on 2007-01-04
i upgrade from a geforce4 to a geforce6 and no problems (X starts just fine, etc.) but it's recognizing the card as a generic VESA card.  i know there's a way to get the system to re-look for a video card like during installation but for the life of me i can't remember how.  any help?

thanks

---

### Post by taurus on 2007-01-04
Just install nVidia driver for it!!!

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by maxamillion on 2007-01-04
```
sudo aptitude install nvidia-glx
sudo dpkg-reconfigure xserver-xorg
```

when you reconfigure, select "nvidia" as the driver .... then restart X.

---

### Post by oldmanstan on 2007-01-04
thank you both, one related problem though... when i run glxgears to get an idea of my framerates nothing gets printed, the gears just spin but no info gets displayed, any ideas?

---

### Post by taurus on 2007-01-04
```
glxgears -printfps
```

---

### Post by oldmanstan on 2007-01-05
well now that was easy, i feel dumb, thank you

---

### Post by ~LoKe on 2007-01-05
> **oldmanstan said:**
> well now that was easy, i feel dumb, thank you

Just for reference, don't rely too much on the output from GLXGears. ;)

---

