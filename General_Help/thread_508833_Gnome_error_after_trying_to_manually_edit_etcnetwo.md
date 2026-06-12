---
title: "Gnome error after trying to manually edit /etc/network/interfaces to set static IP"
date: 2007-07-24
forum: General Help
---

### Post by k_22 on 2007-07-24
Hello.  I tried to set a static NAT IP on my Ubuntu box by editing the /etc/network/interfaces file.  After doing this, I rebooted and I didn't have any connectivity; also, after logging into GNOME all I got was a white square and the desktop never loaded.  

I reset the interfaces file to do dhcp from the command line.   If I boot with an ethernet cable plugged in, I get the same issue after logging into gnome.  If I disconnect the ethernet cable, the white box turns into a dialog box with the following error (see attachment) and gnome loads the desktop normally with IP connectivity.  Has anyone run into this before?  Thanks.

---

### Post by zanglang on 2007-07-25
I'm guessing you had a syntax error in your interfaces file.. Can you try commenting out everything (prepend a '#' in front of each line) in it, and use the GNOME networks administration tool from the Admin menu to configure your static IP? Or, post your /etc/network/interfaces here.

---

