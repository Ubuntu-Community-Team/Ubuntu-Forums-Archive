---
title: "FLEXlm and Hoary 5.04"
date: 2005-05-09
forum: General Help
---

### Post by kolbjorn on 2005-05-09
Just wante to share the solution to a problem I encountered during the installation of IDL 6.0 on Hoary 5.04. After having installed IDL using the non-gui method (xinstall.sh -NOGUI since the GUI-version crashes) I tried to start the FLEXlm. The process just stopped with a single line of text saying the the license manager couldn't initialize.

After hours of playing around, finding no solutions on the net, I finally found it myself: The problem is that you have to create a folder called /usr/tmp, or at least make a link from /tmp to it. That solved the problem.

I hope this might help others since I've seen a lot of people having this problem on Debian type systems.

Regards,
Kolbjorn

---

