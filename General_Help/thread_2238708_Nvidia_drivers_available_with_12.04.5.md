---
title: "Nvidia drivers available with 12.04.5"
date: 2014-08-09
forum: General Help
---

### Post by cscj01 on 2014-08-09
What Nvidia drivers are available for 12.04.5 with the Trusty HWE?  The only one I can find is 173, and this does not support my EVA Geforce GTX 750 TI.  I tried installing the Nvidia driver 334.21, but when I go to a text only terminal (ctrl-alt-F1) and give the command```
sudo service lightdm stop
```I get a message that the script I am trying to run has been converted to an Upstart job and that the X server has not been stopped.  Therefore ```
sudo sh ./NVIDIA-Linux-x86_64-334.21.run
``` fails because there is an X session.  I am at a loss here, because my system is starting up in Low Res mode, and I do not know how to proceed.  Any help would be appreciated.

---

### Post by cscj01 on 2014-08-13
I am closing this as I have successfully upgraded to 14.04.1.

---

