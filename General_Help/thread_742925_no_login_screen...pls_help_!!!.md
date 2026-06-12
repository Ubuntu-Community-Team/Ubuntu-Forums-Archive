---
title: "no login screen...pls help !!!"
date: 2008-04-02
forum: General Help
---

### Post by manga on 2008-04-02
i install ATI graphic driver in this method.........using command line.


sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

after installation...it prompt me to reboot. After rebooting....i cannot see any login in screen. Just a blank screen.I`m using a standalone ATI graphic card in my computer (X800 Radeon). I also have a onboard graphic that come with motherboard.(nvidia). I set my bios to use  the standalone graphic card first.

Now that i can`t see the login screen....what must i do to get back to normal.:confused:Pls help...thanks!!!

---

### Post by kesman on 2008-04-02
Boot to recovery mode and run command:
```

dpkg-reconfigure xserver-xorg

```
and set VESA to be your graphics driver. Now reboot and you should be back in graphical mode. Then fetch an application called Envy from [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu9_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu9_all.deb)

and install it. Then open it and use it to install your ATI driver.

---

### Post by manga on 2008-04-02
> **kesman said:**
> Boot to recovery mode and run command:
```

dpkg-reconfigure xserver-xorg

```
and set VESA to be your graphics driver. Now reboot and you should be back in graphical mode. Then fetch an application called Envy from [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu9_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu9_all.deb)

and install it. Then open it and use it to install your ATI driver.

thanks!....kesman....really appreciate your help.I manage to get it back to normal.

---

### Post by kesman on 2008-04-03
Did you install Envy and did it work as it should?
Try running this in terminal to see if you'r 3d acceleration works:
```

glxinfo | grep rend

```

If it says "direct rendering: yes" then everything's fine.

---

