---
title: "X Server"
date: 2007-06-02
forum: General Help
---

### Post by Erky on 2007-06-02
Hello,
   
    I'm not sure if this is in the right forum. I installed Ubuntu via Wubi earlier today, and it doesn't seem to work right. When I start it, a screen pops up saying something about X Server not starting. When I try to run xinit or startx, I get an error saying

"Fatal server error:
 no screens found.

fatal IO error 104 (connection reset by peer on X server ":0.0' after 0 requests (0 known processed) with 0 events remaining."

I'm running a VisionTek XTASY 9200 series graphics card.

Please help if possible!

---

### Post by useResa on 2007-06-02
You could try, after you received the error and the prompt appears, the following command
```
sudo dpkg-reconfigure xserver-xorg
```

By doing so your settings will be reconfigured.
Hopefully that will solve your issue.

---

### Post by Erky on 2007-06-02
I tried that, and it didn't work.

---

### Post by useResa on 2007-06-02
What driver did you choose for your video card?
You might want to try *vesa* just to get your x server running first.

---

### Post by matigol on 2007-06-02
What is your card ? 

ATI or nvidia ? 

Do you use open source driver or whatever ?

---

### Post by Erky on 2007-06-02
It's an nvidia, but that's not the problem anymore. After I changed the settings, I restarted and when I got to the Ubuntu boot screen it froze and gave me the following:

"BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)

/bin/shi can't access tty; job control turned off"

Then, I tried to reboot in windows, and as soon as I got to the boot-up screen, it gace me a blue screen of death with and UNMOUNTABLE_BOOT_LOAD error.

Please help! This is urgent!

---

