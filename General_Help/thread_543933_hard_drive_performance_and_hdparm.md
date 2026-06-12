---
title: "hard drive performance and hdparm"
date: 2007-09-05
forum: General Help
---

### Post by richardy on 2007-09-05
Hi,
I recently checked the hardware performance on my xubuntu, feisty fawn installation using hdparm and found it to be running rather slow due to none of the options being used so i tried the command hdparm -d1 -u1 -m16 -c3 /dev/hda and this made a huge improvement to the disk read speed. I then put this line into /etc/hdparm.conf, saved and rebooted. However when i checked the settings again using hdparm nothing had changed. Shouldn't this have worked? Do i need to do something else to have these settings implemented permanently. Any help would be much appreciated.

Cheers.

---

### Post by squaregoldfish on 2007-11-11
Not sure if this will work or not, but try this:

sudo update-rc.d hdparm defaults

Steve.

---

