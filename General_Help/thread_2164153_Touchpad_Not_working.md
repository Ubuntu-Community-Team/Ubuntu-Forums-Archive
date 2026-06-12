---
title: "Touchpad Not working"
date: 2013-07-30
forum: General Help
---

### Post by 3pFpbJe on 2013-07-30
Hello all,

Recently after installing the Leap Motion SDK my computer touchpad stopped functioning while I am using my Ubuntu 12.04 partition (I am dual-booting with Windows). The touchpad works completely fine when I am in Windows, but for some reason it is not responsive at all when I am in Ubuntu. I have to plug in a mouse via USB to maneuver around (beside using terminal). I have enabled my touchpad by going to 'xinput' on terminal, as some other forum post suggested, but my touchpad still is not working. What can I do to fix this?

Thanks for the help!

---

### Post by t0p on 2013-07-30
Possible solution: press F6. That often activates/deactivates touchpads.

If you've tried that, or it doesn't work, I don't know.

---

### Post by mojo706 on 2013-07-30
Hello, Try this solution [http://ubuntuforums.org/showthread.php?t=1971196](http://ubuntuforums.org/showthread.php?t=1971196) and if it does not work try

```
sudo apt-get install xserver-xorg-input-synaptics
```

Let us know if all goes well.

---

