---
title: "spin down hard drive"
date: 2005-05-09
forum: General Help
---

### Post by dave9191 on 2005-05-09
Ok, Im using an old laptop as a server machine. Its all nicely configured with ubuntu server install. 

But since the server is a private one and not in constant demand id like to spin down the hard drive when its not in use to extend the life of this old antique. 

I know that ubuntu spins the HDD down on my other laptop when im running on batteries, how can i get my server laptop to do that when its running on full power. And a little note, since its a server install i dont think it installed any laptop support etc...


Dave

---

### Post by eivind on 2005-05-09
Quick tip:

sudo apt-get install hdparm (if it's not there already)
cd /etc/init.d
nano hdparm

In this file, you add the following lines:
#!/bin/sh
hdparm -S 240 /dev/hda

Of course, assuming that /dev/hda is your hard drive.

Next, quit and save:
Ctrl+X
Y

Make this script start at startup:

update-rc.d hdparm defaults

Now, you can start hdparm by doing 
sudo /etc/init.d/hdparm

At least, I think so. This way of doing it will also make your harddisk spin down after 20 minutes whenever you start your laptop.

---

### Post by dave9191 on 2005-05-09
Thanks eivind, you are a star :)

---

### Post by VerteX on 2005-07-15
This is an awesome post. It works and now my harddisk doesn't spin down every 10 seconds when it's on battery power
Instead of 240 in "hdparm -S 240 /dev/hda" I used 60 to set it to 5 minutes. 240 I believe sets it to 20 minutes.
 \\:D/ 
Very helpful! Thanks! (This post ought to be in the "HOW-TO" forum section)

---

