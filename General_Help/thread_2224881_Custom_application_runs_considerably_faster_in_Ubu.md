---
title: "Custom application runs considerably faster in Ubuntu 8 vs Ubunto 14"
date: 2014-05-18
forum: General Help
---

### Post by Mike_Soultanian on 2014-05-18
We have a custom (non-graphical) application that processes images received from a gigabit camera and then sends the data to a central server.  The application currently runs on an old Ubuntu 8 installation and I'd really like to get it off of that because it was built years ago and 8 is end-of-life.  I installed a new version of Ubuntu (14.04 Server LTS) on another box with identical hardware and I'm seeing 80% CPU utilization on the Ubuntu 8 box and 110% CPU on the Ubuntu 14 box - should there really be that big of a difference between the two?  I think I'm gonna swap the drives between the two boxes to make sure it's not a hardware issue, but I thought I'd throw out the question and see if anyone had any input.

These are the details on the two versions:

irtracker@irtracker-sap-11:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04 LTS
Release:        14.04
Codename:       trusty

~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy

Any ideas?

Thanks!
Mike

---

### Post by Mike_Soultanian on 2014-05-18
So I swapped the drive with Ubuntu 8 into the machine that was running Ubuntu 14 to make sure it wasn't a hardware issue, and it's still running faster with a difference of 20-30 on the %CPU column in top.  Any ideas?  I'd really like to upgrade all of these computers to the newer version of Ubuntu, but I gotta be careful because image processing is processor-intensive and I gotta save as many CPU cycles as I can.

Thanks!
Mike

---

### Post by Mike_Soultanian on 2014-05-18
btw, would a server install be optimized any differently than a minimal or desktop install?  I'm not sure what was used for the Ubuntu 8 install, but I used server for the Ubuntu 14 install.

---

### Post by Impavidus on 2014-05-18
The difference in CPU usage doesn't necessarily mean that Hardy is faster than Trusty. If Trusty needs more CPU cycles to do the same processing, Hardy is faster if you get limited by CPU. If Trusty can handle I/O faster than Hardy, than Trusty has more data available for processing each second, leading to a higher fraction of CPU cycles utilised than on Hardy, that is, a higher CPU load and faster processing – and not necessarily any speed difference if you get CPU limited. You have to properly time the process.

In these examples you were probably not limited by CPU.

---

### Post by Mike_Soultanian on 2014-05-19
Thanks for the info!  So I looked at how long it's taking to run the main loop and 14.04 is hovering around 2.0ms and 8.04 is hovering around 2.1ms.  Like you said, it isn't a problem until you get limited by CPU, but it would be nice to keep those numbers as low as possible, and it seems like lower is possible on 8.04.  I'm trying to figure out if that's just 14.04 doing come kinda OS/CPU optimization, or if there was some configuration setting that I should be looking at.

Would it many any difference if I picked the desktop or minimal install vs server?

Thanks!
Mike

---

