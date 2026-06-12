---
title: "RDP gives blue screen"
date: 2019-10-29
forum: General Help
---

### Post by optimusnog on 2019-10-29
I have a fresh image of Ubuntu 18.04.3 installed with Xrdp.  I have followed a number of guides online on how to properly install Xrdp for 18.04 by installing Xorg, Xfce4, etc. I have googled the blue screen issue to death and tried just about every fix out there, yet I cannot solve the problem.  I see the connection being established in the logs, but the RDP client on the windows side always gets a blank blue screen.  I have had a number of expert Linux co-workers attempt to solve the problem to no avail.  

Is there anyone out there who has gotten Xrdp or rdesktop to work with Ubuntu 18.04.3 and if so, how?

---

### Post by dragonfly41 on 2019-10-29
Does this tutorial help?

[https://linuxize.com/post/how-to-install-xrdp-on-ubuntu-18-04/](https://linuxize.com/post/how-to-install-xrdp-on-ubuntu-18-04/)

Also to monitor ports etc. I suggest this command to scan localhost

gksu zenmap

---

### Post by optimusnog on 2019-10-30
This was the first of many guides I tried following.  It did not work.  Funny enough I was able to  get it to work with Mate, but it must be possible to get it to work with Gnome?

---

### Post by HermanAB on 2019-10-30
Bear in mind that the standard way to remote manage UNIX systems is with SSH.   On Windows, you can use winscp to connect to a SSH server.

Any Windows RDP mechanism will have very limited support, so YMMV.

---

