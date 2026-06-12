---
title: "Ubuntu 8.04, X11, and VNC"
date: 2008-06-17
forum: General Help
---

### Post by bbarcelo on 2008-06-17
I just installed Hardy Heron and have encountered a problem that was not present in any earlier version. After setting Ubuntu to auto-login as a selected user and enabling VNC, I can't simply boot up the computer and get to VNC. This is caused by some problem with X11 recognizing my monitor, of which I have none, and stops ubuntu-desktop from loading as a result of some prompt that notifies me of Ubuntu's failure to find a monitor present.

My question is this: How can I set up my Ubuntu 8.04 installation to be plugged in anywhere with a network connection and a power source, have it boot up and be accessible without a monitor via VNC.

Doing this exact thing in Ubuntu 7.10 took me about four minutes and I've Googled all I can to find out any way to do this in 8.04. I hope this is some easy fix :confused:

Thanks for any help!

---

### Post by bbarcelo on 2008-06-18
Just ended up changing to an nVidia graphics card and using the nvidia-settings tool. The ATI card was giving me a lot of grief for whatever reason and was causing all this.

---

