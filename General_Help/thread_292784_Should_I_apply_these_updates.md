---
title: "Should I apply these updates??"
date: 2006-11-04
forum: General Help
---

### Post by JayTee on 2006-11-04
When I got up this morning my system had the updates icon in the system tray to alert me to pending/available updates. There were five packages available. Since it took me awhile to get Beryl working with XGL on my Nvidia card and later on almost 10 hours to get the right resolution on my new widescreen monitor I'm a little hesitant to allow these updates for fear of them breaking something. The old addage being, "If it ain't broke, don't fix it!" What worries me the most is that if I do allow them I might not be able to get back to my present configuration.
I'm listing them here:
libimlib2
new version 1.2.1-2ubuntu0.1
linux-restricted-modules-2.6.15-27-386
new version 2.6.15.12-1
linux-restricted-modules-2.6.15-27-686
new version 2.6.15.12-1
linux-restricted-modules-common
new version 2.6.15.12-1
nvidia-glx
NVIDIA binary XFree86 4.x/X.Org driver
new version 1.0.8776+2.6.15.12-1

---

### Post by bollix47 on 2006-11-04
I applied those updates this morning knowing there was a chance that X might 'break' as it was mentioned on the guide that I used to install latest nvidia driver. Of course, it did break.

I logged in and went to the folder where the driver was located and ran:

sudo sh NVIDIA*.run

After it finished I rebooted and all was fine again.

I don't have beryl so not sure if your experience will be different.

---

### Post by mega on 2006-11-04
it broke mine too

I downloaded/installed the nvidia beta driver and that fixed it

---

### Post by ferd on 2006-11-04
I applied these updates with no problems.

---

### Post by JayTee on 2006-11-04
Thanks everyone for the info. I think I'm gonna hold off on installing them until I can find some more info on reverting back to previous libraries and drivers. 
To bollix47: what folder is the driver in?
To mega: where did you download the nvidia beta driver from and what version is it?
Does anyone know if there are plans to build in a "rollback" feature like Windows has? It would be nice if there was a command you could run from terminal that would watch whatever changes while you update and be able to reverse the changes if things went south. Since this computer is now running with 1440x900 resolution with XGL and Beryl and all my multimedia stuff works the way I want it to I'm not gonna risk borking the whole thing.

---

### Post by mega on 2006-11-04
I applied the updates and X would not start

I got the nvidia beta driver via google

---

### Post by bollix47 on 2006-11-04
> **JayTee said:**
> 
To bollix47: what folder is the driver in?



I had downloaded the driver from [here]("http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9625.html") when I updated to the latest nvidia beta driver.

---

