---
title: "Pc will not boot to desktop at first turn on."
date: 2014-10-28
forum: General Help
---

### Post by frank18 on 2014-10-28
Hi guys;i have an old P4 with Xubuntu 14.04 installed and lately  it wont go to Desktop it stays on a black screen at first turn on, i have to turn off power and turn on  second time then it boots to Desktop,beside that it runs fine,Any help will be apreciated

---

### Post by yancek on 2014-10-28
I had a similar problem with Ubuntu 14.04 but it would boot to a screen with a garbled screen, horizontal dashes across the top half of the screen.  This happened on cold boots for about two weeks.  I then installed different graphics drivers as I have an nvidia graphics card and it mostly works now.  Not sure how you get to that in Xubuntu, if you have system settings or some type of Control Center to update graphics drivers.

---

### Post by mörgæs on 2014-10-29
In order to give a precise answer we need to know all hardware specifications. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by frank18 on 2014-10-30
Thanks guys i appreciate; i found the Issue, it was a USB extender cable adapter that i had connected to one of the USB ports for easier access so i removed it and now it runs fine.

---

