---
title: "[HELP] Black screen when booting"
date: 2007-11-03
forum: General Help
---

### Post by knightinarms on 2007-11-03
I have the latest Ubuntu 7.10. I loaded the live cd, and then installed. After installing and rebooting the system worked fine. But then I got a message saying drivers were being restricted (or something like that), so I installed the ait drivers, and then the computer was saying I needed to restart to finish the process. So I did. But when it restarted it did the whole Ubuntu loading bar thing, then the screen turned black. And my monitor told me that "nonpresent mode".

I have a radeon x1600. [http://ati.amd.com/products/RadeonX1600/index.html](http://ati.amd.com/products/RadeonX1600/index.html). I tryed loading in safe mode, but honestly I have no idea what to type or do to fix it. Please help me. Thanks.

---

### Post by knightinarms on 2007-11-03
I tryed going to safe mode and typing startx but I got the same thing, also I tryed pressing Ctrl+Alt+F1 but nothing.

---

### Post by knightinarms on 2007-11-03
used the sudo dpkg-reconfigure xserver-xorg and fixed the problem but now I can't change the resolution.

---

### Post by pacsum on 2007-11-03
To fix the no boot splash I did the following
1) Open Terminal
2) Type:   sudo gedit /etc/usplash.conf and change the resolution to 1024x768
3) sudo update-initramfs -u -k `uname -r` 

That's it.

---

### Post by knightinarms on 2007-11-03
Thank you. I'm going to try that. I just reistalled ubuntu and updated everything then reistalled the driver and I'm at the same problem I was before I took pictures this time of what I did:

But I'm going to try your tip.

---

### Post by knightinarms on 2007-11-03
I tryed what you said but the resolution was already set to that 1280x1024. wierd this time though... all the fonts were so small it looked like the res had been set to 1024x1280 instead of 1280x1024. Anyways after rebooting now it just stops at:

Starting Up
Loading...

So... What's going on?

---

