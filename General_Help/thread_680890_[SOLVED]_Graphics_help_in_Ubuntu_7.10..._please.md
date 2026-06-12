---
title: "[SOLVED] Graphics help in Ubuntu 7.10... please"
date: 2008-01-28
forum: General Help
---

### Post by Aaron_M_E on 2008-01-28
Hello all,

I recently converted one of my desktops (being used as a server) to Ubuntu 7.10 from Windows XP. When I first installed Ubuntu I had an issue with the ATI driver but fixed it using a fix I found in a blog. The fix worked for a few weeks and all of a sudden one morning I turned on the monitor and the display is all messed up. The thing is that I am able to see the login area (shadows mainly) and login to the machine. Once logged in I start a vnc session from my laptop and am able to work on the machine no problem. As I am changing screen through vnc I can see the colour changing on the monitor of the linux box. From the bit I understand this issue could have been cause if there was an update to the kernel recently and thus messed up my video.

Does anyone have any suggestions? Anything would be greatly appreciated!

PS. I am comfortable with the command line as I have done work on Unix (limited but familiar)

---

### Post by cdenley on 2008-01-28
If it is a server, you can try the vesa driver since you don't need good video performance, you just need it to work. Are you using ati or fglrx? You can change your video driver and settings by running the command "sudo dpkg-reconfigure xserver-xorg".

---

### Post by Aaron_M_E on 2008-01-28
I am actually using Desktop not server. If I remember correctly, I'm using the fglrx because the ati wouldn't work properly. I will try to run the "sudo dpkg-reconfigure xserver-xorg" command and see what luck I have with that.

---

### Post by Aaron_M_E on 2008-02-07
That fixed it, at least I have a display now. Still will only run in low graphics mode and nothing larger then 800x600 resolution (currently using fglrx) but I probably just have to reinstall the ATI driver for the card/play around with it... and hope things don't screw up again.

Thanks for your help.

---

