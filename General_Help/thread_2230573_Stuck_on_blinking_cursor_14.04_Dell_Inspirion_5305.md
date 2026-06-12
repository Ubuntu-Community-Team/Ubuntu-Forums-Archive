---
title: "Stuck on blinking cursor 14.04 Dell Inspirion 5305"
date: 2014-06-19
forum: General Help
---

### Post by dustin11 on 2014-06-19
Just recently put ubuntu on this machine for my wife. I ordered a Gforce 210 video card for it and installed it with no issues. Everything was running fine when I did a restart and it refused to boot. It will give me the message "USBhid 4-2.3:1 Couldn't find an input interrupt endpoint". I have tried unplugging all the usb devices from the machine and it just freezes. IT will still show me the Ubuntu splash screen when shutting down, after i push the power button. 

Thanks Dustin

---

### Post by dustin11 on 2014-06-20
Seems to be something to do with the X server driver for the Gforce card. I uninstalled the card and just used the Built in graphics and it booted fine. So I uninstalled the two invidia drivers that i installed and rebooted to make sure it would come back up. I then reinstalled the video card and it booted with the video card installed. 
Problem solved!

---

