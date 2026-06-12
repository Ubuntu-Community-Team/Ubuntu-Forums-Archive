---
title: "Special Drivers"
date: 2012-11-06
forum: General Help
---

### Post by Knowlesenator on 2012-11-06
I have a fresh install of Ubuntu 12.04 and I want to enable my graphics drivers so I can play games.  Right now there are two options within the Special Drivers area of System Settings: The graphics driver and the graphics driver (post release updates).  It sounds like I want the post release updates but whenever I click to enable it I get this message: look in var/log/jockey.log.  Does anyone know what I should do?  I have attached two photos that show the screens.

---

### Post by strafe_sawdoffe on 2012-11-06
I'd start here, with step 2.1: 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

or, here:

[http://askubuntu.com/questions/142627/flgrx-amd-catalyst-driver-issues-in-ubuntu-12-04](http://askubuntu.com/questions/142627/flgrx-amd-catalyst-driver-issues-in-ubuntu-12-04)

They're basically the same thing, but the first method is more detailed and includes things like purging the old drivers and backing up your current configuration. If you were never able to get the drivers activated in the first place, then some of those steps may not apply and you could just try the second link.

---

### Post by supergrav on 2012-11-06
Can you post contents of jockey.log ?

---

### Post by Knowlesenator on 2012-11-07
Thank you very much.  I followed those steps and my graphics card is enabled and working.

---

