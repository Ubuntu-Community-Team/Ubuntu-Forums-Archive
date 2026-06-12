---
title: "shutdoen procedure"
date: 2008-02-20
forum: General Help
---

### Post by ltlbgr67 on 2008-02-20
Hi,
I am running a dos program in dosemu.  The program runs a for next loop to print to labels to a thermal printer.  I print these labels by the thousands.  In the program I open the lpt1: as an output device.
Ubuntu must spool the print jobs (I cant find where).  My problem is if the labels were not printed and ubuntu is shutdown, on reboot it starts the spool all over again.
I can cancel the print jobs from the terminal  "cancel -a", but would like to:

Best choice - when ubuntu is shutdown for it to run "cancel -a" (cancel all print jobs) automatically or

Have an Icon on the desktop that can be clicked to run the cancel.

I am not the only one using this and as I am new to ubuntu the other staff members are not computer savy and am trying to make this as easy for all.

I hope I explained myself sufficiently for any help that would be greatly appreciated.

---

### Post by freelinuxhelp on 2008-02-20
All shutdown scripts are located in /etc/rc0.d/ and all reboot scripts are located in /etc/rc6.d/

This should set Ubuntu to cancel all print jobs on shutdown or reboot. Run these in a terminal window:

```
sudo echo '#!/bin/sh' > /etc/init.d/cancelprint
sudo echo 'cancel -a' >>/etc/init.d/cancelprint
sudo echo 'exit 0' >> /etc/init.d/cancelprint
sudo chmod +x /etc/init.d/cancelprint
sudo ln -s /etc/init.d/cancelprint /etc/rc0.d/K01cancelprint
sudo ln -s /etc/init.d/cancelprint /etc/rc6.d/K01cancelprint
```

---

### Post by ltlbgr67 on 2008-02-20
Thank you freelinuxhelp.

I tried running the code and am getting a permission denied error.  I assume this has to do with it not asking for password.

---

### Post by freelinuxhelp on 2008-02-21
Could you post the output from the command that gave the error?

---

