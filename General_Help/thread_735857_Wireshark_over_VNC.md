---
title: "Wireshark over VNC"
date: 2008-03-26
forum: General Help
---

### Post by g.caltech on 2008-03-26
Hello,
I am running 7.10. I have configured Xvnc to allow remote VNC connections which works well.
However, when I try to start wireshark in a VNC session, I get a segmentation fault.
If I start wireshark from the local monitor and keyboard session, it runs properly.
I am able to run tshark in the VNC session, so it seems to be an issue with the GUI.
Can anyone verify if wireshark works within a VNC session? Is there additional configuration necessary?
I originally installed Kubuntu, but then installed Gnome which I am now using, so I am wondering if this is causing the conflict.
Thank you,
g

---

### Post by beatbros on 2008-03-26
Hi,
here ubu 7.10, Gnome, Wireshark Version 0.99.6,
Running on Linux 2.6.22-14-generic works in VNC session without errors and no extra-configuration has been applied.

If you launch wireshark as user or root did you notice any difference?

Bye

---

### Post by g.caltech on 2008-03-26
> **beatbros said:**
> Hi,
here ubu 7.10, Gnome, Wireshark Version 0.99.6,
Running on Linux 2.6.22-14-generic works in VNC session without errors and no extra-configuration has been applied.

If you launch wireshark as user or root did you notice any difference?

Bye

I tried both wireshark and sudo wireshark and both gave seg faults. I guess my installation is hosed, so I will try to reinstall.

---

