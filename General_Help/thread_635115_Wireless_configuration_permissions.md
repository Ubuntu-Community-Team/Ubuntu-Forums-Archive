---
title: "Wireless configuration permissions"
date: 2007-12-08
forum: General Help
---

### Post by booyabazooka on 2007-12-08
I'm realizing that the Linux permissions system doesn't quite make sense when it comes to configuring laptop hardware.  It would typically make sense that any device configuration requires root, so not any user can ssh into my box and mess with stuff that affects other users.  However, if I lend my notebook to someone, that user needs to be able to reconfigure the wireless interface wherever he goes.

I shouldn't have to give him a root account for this.  I think the perfect solution would be to only allow network commands (iwconfig, ifconfig, dhclient) for a user who is either root OR is logged into the physical box (not remotely).  As I see it, anyone who is sitting at my notebook should be able to run iwconfig.  Is this possible?

---

### Post by cmnorton on 2007-12-08
Are you running Network Manager? I thought Network Manager would allow connection to "other" wireless network. I cannot remember typing in a password for that.

---

### Post by booyabazooka on 2007-12-08
Unfortunately, I have had very little luck getting the networking gui to work properly.  It has a myriad of problems, The "Network" gui (which requires root anyway) has a tendency to not make a low-level connection at all. "Roaming mode" crashes (the icon disappears) when I try to connect to an "other" network, and will frequently make a connection with the AP but fail to transfer any data.

But, this is not what I wish to inquire about.  I am quite happy to give up on the UI, as I know the world will always have UI bugs. I have written a shell script to connect to the several wireless profiles that I use, and this works fine.  I would just like to re-permission it somehow.

---

