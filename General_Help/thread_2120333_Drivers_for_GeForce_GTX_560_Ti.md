---
title: "Drivers for GeForce GTX 560 Ti"
date: 2013-02-26
forum: General Help
---

### Post by nesoor on 2013-02-26
Yesterday I was trying to set my resolution on 1920x1080 but every time when I started a game or did a restart the resolution went back to 1024x768.

I had also some graphic problems with some games so I tried to install a different driver from the additional drivers list.

There were around 5 or 6 different drivers. 
I choose for the X.Org X server which was a bad idea, this driver worked better until I restarted my computer.

Now it's not even possible to change my resolution at all, not even in the Display settings.

Also the "Additional drivers" list is empty. 
Every driver disappeared I just have an empty list now.
How can I fix this?

Ubuntu 64bit 12.10

**UPDATE!**
Finally I got some updates from nvidia so I installed them.
I restarted my computer and there was the list again.
I tried to install the nvidia driver again and had to restart the computer. 
After the pc started again nothing changed and the list was empty again.
No drivers installed or anything else.

**UPDATE**
I can install the Nvidia drivers from the ubuntu software center.
When I do this and install the nvidia driver I have to restart my pc after that still nothing changed and no Nvidia driver is installed

---

### Post by albandy on 2013-02-26
> **nesoor said:**
> Yesterday I was trying to set my resolution on 1920x1080 but every time when I started a game or did a restart the resolution went back to 1024x768.

I had also some graphic problems with some games so I tried to install a different driver from the additional drivers list.

There were around 5 or 6 different drivers. 
I choose for the X.Org X server which was a bad idea, this driver worked better until I restarted my computer.

Now it's not even possible to change my resolution at all, not even in the Display settings.

Also the "Additional drivers" list is empty. 
Every driver disappeared I just have an empty list now.
How can I fix this?

Ubuntu 64bit 12.10

Can you tell us your graphic card model?

---

### Post by nesoor on 2013-02-26
> **albandy said:**
> Can you tell us your graphic card model?

Thanks for your reply! :)

GeForce GTX 560 Ti (Gigabyte)

---

### Post by albandy on 2013-02-27
Try this:
sudo apt-get install nvidia-current
then reboot and check if the driver list appears again.

---

### Post by mörgæs on 2013-02-27
Changed the title to a more informative one.

---

### Post by Armann on 2013-02-27
I just setup Nvidia drivers for 260GTX.
I downloaded the driver from [http://www.geforce.com/drivers](http://www.geforce.com/drivers)
Not everyone wants to use proprietary drivers but it worked fine :)

If you want to go that route:
sudo apt-get install build-essential linux-source
sudo apt-get install linux-headers-`uname -r`

Ctrl+Alt+F2 and find the downloaded driver and run it sudo sh drivername.

Written from memory so maybe I don't remember everything.

Another easier way is this:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

Reboot..

---

