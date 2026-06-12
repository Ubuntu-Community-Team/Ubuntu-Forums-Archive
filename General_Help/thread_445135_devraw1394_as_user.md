---
title: "/dev/raw1394 as user"
date: 2007-05-15
forum: General Help
---

### Post by cotcot on 2007-05-15
I have installed dvgrab-2.1 (compiled from source because kdenlive asks for a later version than 1.8 provided by the repos). When I switch on the camcorder on firefire I cannot capture video before changing permissions : ```
sudo chmod 755 /dev/raw1394
```
Is there anything I can change to avoid that i have to change permissions each time I capture video ?
Thanks

---

### Post by cotcot on 2007-05-16
Problem is solved. After checking the udev rules I created a group "disk" and added the user to it. Reboot and problem was solved.

---

