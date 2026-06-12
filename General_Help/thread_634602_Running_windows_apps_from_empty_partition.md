---
title: "Running windows apps from empty partition"
date: 2007-12-07
forum: General Help
---

### Post by rkrug on 2007-12-07
I'm currently making the switch back to Ubuntu (which I ran for two years until switching back to windows), and I wanted to know if I'd be able to run windows applications from another partition that doesn't have windows on it. Like, if I copied the program files from windows to an empty partition before I install Ubuntu could I cd to the directory and use wine to run the program?

I really don't want to have to install the programs again on Ubuntu since I'm not sure where my I put the CDs. 

Thanks,
Rob

---

### Post by derby007 on 2007-12-08
What about virtualisation? U could stay in Ubuntu & fire up some Virtualization program: VMWare, VirtualBox, and run windows that way....

---

### Post by rkrug on 2007-12-08
Yes, I could do that, but what I'm trying to do is run them without using windows at all.

---

### Post by geirha on 2007-12-08
It depends on the application itself, whether it needs certain things to be present in the registry or not. Also, not all windows applications will run with wine. Look up your applications at [http://appdb.winehq.org](http://appdb.winehq.org) to see how well each application works.

You can test this on the liveCD, so you'll know whether it will work or not. When the liveCD is running, install wine, mount up all the windows partitions, cd into program\ files/the_app/ and run the application with "wine the_app.exe"

---

