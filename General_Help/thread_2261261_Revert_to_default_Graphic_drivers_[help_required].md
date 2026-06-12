---
title: "Revert to default Graphic drivers [help required]"
date: 2015-01-17
forum: General Help
---

### Post by soumoks on 2015-01-17
Hello, I recently purchased a lenovo z50-70 623 laptop with Nvidia 820m graphic card and installed ubuntu 14.04 on it.
It provided me with a proprietary driver for nvidia under additional drivers and I switched to it.However, after a reboot the display freezes after 5 minutes or so.

Is there anyway to switch to the default driver using the command line from a live cd?, because now the display is freezing as soon as I switch on the device.
Thanks

---

### Post by monkeybrain20122 on 2015-01-17
It should be easy if you have not followed some outdated tutorial and manually blacklisted the nouveau driver. Just remove  all the Nvidia packages with synpatic and then remove or rename /etc/X11/xorg.conf. After reboot it should revert to the open driver.

More info here [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

---

### Post by Frogs Hair on 2015-01-17
You can accomplish this from the additional drivers  utility as well if the proprietary driver was installed from there. Just select it for removal.

---

### Post by soumoks on 2015-01-17
Actually the screen would freeze as soon as I typed in additional drivers in the search menu,that's why I needed a command line version.
However,tried once again and the screen didn't freeze luckily,reverted back to the default driver :)

Thank you both :)

---

